MIDISequencer
===

MIDI Sequencer that sends MIDI events to other apps.  
Built top on [`AKSequencer`](https://github.com/AudioKit/AudioKit/blob/master/AudioKit/Common/MIDI/Sequencer/AKSequencer.swift) of [AudioKit](https://github.com/AudioKit/AudioKit) for iOS and macOS.  
Create smart MIDI sequencer instruments with just focus on notes.

Requirements
----

- Swift 3.0+
- iOS 9.0+
- macOS 10.11+

Install
----

``` ruby
pod 'MIDISequencer'
```

Usage
----

MIDISequencer built top on `AudioKit`'s `AKSequencer` with [`MusicTheory`](https://github.com/cemolcay/MusicTheory) library to create sequences just focusing on notes with multiple track support.

- Create a `MIDISequencer` instance.  

``` swift
let sequencer = MIDISequencer(name: "Awesome Sequencer")
```
  
- Create a `MIDISequencerTrack` and add it to sequencer's tracks.  

``` swift
let track = MIDISequencerTrack(
	name: "Track 1", 
	midiChannel: 1)
```

- Add some `MIDISequencerStep`s to track's `steps`

``` swift
track.steps = [
	MIDISequencerStep(
	  note: Note(type: .c, octave: 4),
	  noteValue: NoteValue(type: .quarter),
	  velocity: .standard(100)),
	MIDISequencerStep(
	  note: Note(type: .d, octave: 4),
	  noteValue: NoteValue(type: .quarter),
	  velocity: .standard(100)),
	MIDISequencerStep(
	  note: Note(type: .e, octave: 4),
	  noteValue: NoteValue(type: .quarter),
	  velocity: .standard(100)),
	MIDISequencerStep(
	  note: Note(type: .f, octave: 4),
	  noteValue: NoteValue(type: .quarter),
	  velocity: .standard(100)),
	]
```

- You can even add chords or multiple notes or even both to any step.

```
MIDISequencerStep(
  chord: Chord(type: .maj, key: .c),
  octave: 4,
  noteValue: NoteValue(type: .quarter),
  velocity: .standard(60))
  
MIDISequencerStep(
  notes: [Note(type: .c, octave: 4), Note(type: .d, octave: 4)],
  octave: 4,
  noteValue: NoteValue(type: .quarter),
  velocity: .standard(60))
  
MIDISequencerStep(
  notes: Chord(type: .maj, key: .c).notes(octave: 4) + [Note(type: .c, octave: 4), Note(type: .d, octave: 4)],
  noteValue: NoteValue(type: .quarter),
  velocity: .standard(60))
```

- Set `isMuted` property to `true` to mute any `MIDISequencerStep`.
