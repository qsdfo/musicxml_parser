# MusicXML parser

## Installation

    pip install musicxml_parser

## Usage

    from musicxml_parser.scoreToPianoroll import scoreToPianoroll
    score_path = "test.xml"
    quantization = 16
    pianoroll, articulation = scoreToPianoroll(score_path, quantization)

## Description :
Music XML parser written in Python based on a SAX analyzer.
Given an mxml file, outputs three dictionaries indexed by instruments names. For each instrument, three Numpy arrays are created :
- a binary pianoroll (note on/off along time given a certain rhythmic quantization)
- a binary articulation which is the same matrix as the pianoroll but with shorter duration so that we can distinguish between a long note or several repeated occurences of the same note. Hence, if a quarter note lasted 4 frames in the pianoroll it would be 3 in the articulation. Staccati notes are 1 whatever their duration.
- a dynamic vector which indicate the evolution of the dynamic for this instrument along time

Written in python 2.7

## Packages dependencies :
* numpy

## Files
The main function is ScoreToPianoroll in ScoreToPianoroll.py
It takes as input the path to a MusicXML file and output two python dictionnary of the form :

    {'track_name' : matrix}

where matrix is two-dimensional, first axis begin the time, second the pitch.