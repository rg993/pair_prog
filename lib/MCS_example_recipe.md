# {{PROBLEM}} Multi-Class Planned Design Recipe

## 1. Describe the Problem

As a car owner
So that I can keep a record of details about my tyres
I want to keep track of the tyres individually, by their position on my car

As a car owner
So that I have the two important pieces of data for a tyre
I want to be able to record both tyre pressure and tyre tread depth

As a car owner
So that I have a history of tyre readings
I want to be able to keep a record of historical readings, when those were, as well as current readings

As a car owner
So that I can see the details of my car at a glance
I want to list the tyres' positions, latest readings and when those were


## 2. Design the Class System

nouns: car, tyre, position, pressure, historical readings, current readings, 
verbs: add pressure, add tread depth, list tyre positions, list dates, list tyre pressures

_Consider diagramming out the classes and their relationships. Take care to
focus on the details you see as important, not everything. The diagram below
uses asciiflow.com but you could also use excalidraw.com, draw.io, or miro.com_

```
┌────────────────────────────┐
│ car                        │
│ 
                             │
│ - tyre readings  (list of dictionaries) (pressure, tread depth)                  │
│ - add(track)               │
│ - search_by_title(keyword) │
│   => [tracks...]           │
└───────────┬────────────────┘
            │
            │ owns a list of
            ▼
┌─────────────────────────┐
│ Tyre.                   │
│                         │
│ - position              │
│ - pressure, tread depth │
│ - format()              │
│   => "TITLE by ARTIST"  │
└─────────────────────────┘
```

_Also design the interface of each class in more detail._

```python
class MusicLibrary:
    # User-facing properties:
    #   tracks: list of instances of Track

    def __init__(self):
        pass # No code here yet

    def add(self, track):
        # Parameters:
        #   track: an instance of Track
        # Side-effects:
        #   Adds the track to the tracks property of the self object
        pass # No code here yet

    def search_by_title(self, keyword):
        # Parameters:
        #   keyword: string
        # Returns:
        #   A list of the Track objects that have titles that include the keyword
        pass # No code here yet


class Track:
    # User-facing properties:
    #   title: string
    #   artist: string

    def __init__(self, title, artist):
        # Parameters:
        #   title: string
        #   artist: string
        # Side-effects:
        #   Sets the title and artist properties
        pass # No code here yet

    def format(self):
        # Returns:
        #   A string of the form "TITLE by ARTIST"
        pass # No code here yet

```

## 3. Create Examples as Integration Tests

_Create examples of the classes being used together in different situations and
combinations that reflect the ways in which the system will be used._

```python
# EXAMPLE

"""
Given a library
When we add two tracks
We see those tracks reflected in the tracks list
"""
library = MusicLibrary()
track_1 = Track("Carte Blanche", "Veracocha")
track_2 = Track("Synaesthesia", "The Thrillseekers")
library.add(track_1)
library.add(track_2)
library.tracks # => [track_1, track_2]
```

## 4. Create Examples as Unit Tests

_Create examples, where appropriate, of the behaviour of each relevant class at
a more granular level of detail._

```python
# EXAMPLE

"""
Given a track with a title and an artist
We see the title reflected in the title property
"""
track = Track("Carte Blanche", "Veracocha")
track.title # => "Carte Blanche"
```

_Encode each example as a test. You can add to the above list as you go._

## 5. Implement the Behaviour

_After each test you write, follow the test-driving process of red, green,
refactor to implement the behaviour._
