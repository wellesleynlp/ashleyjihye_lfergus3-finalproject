# Melody Generation From Lyrics
Leah Ferguson, Ashley Thomas

https://drive.google.com/open?id=0B2L-MQr1YVbbQzdKWFAtb2lId2c

CS349 Final Project

###Project Update (4/6/16)

During the last few weeks, we spent most of our time doing further background reading, honing our original idea, and then trying to parse our raw data into a usable format. Our background research brought several issues to our attention. We were forced to think about the difference in transposing major and minor keys, working with pitches of notes versus intervals, and retrieving syllables orthographically versus phonetically (using the CMU Dictionary). We decided to store intervals instead of pitches, and we think this will provide a more natural flow to our piece and be more forgiving in cases of error. We also decided on taking syllables orthographically, with a plan to expand to phonetic data down the line. We also realized that most of the work done previously with lyrics and music was related to the overall sentiment of an overall piece of text. For example, someone took overall sentiments of books and then used a formulaic method (based on previous research on sentiments in music) to generate melodies.

We also shifted our idea a bit from our original goal. We first wanted to generate a melody based on the meanings of words, but realized that this was more akin to machine translation between English words and melodies. We are intrigued by this idea, but given the time constraints and our limited knowledge of machine translation, we decided to pursue generating melodies based on rhythms/syllables of words instead. Our goal now is to generate melodies that "fit" the natural flow of words, creating a song that is easy to sing and sounds pleasant and natural.

In terms of data, we procured our original data in the form of mxl files, and we spent time figuring out how to mass-convert them to xml files, which would make it possible to collect data from them. Next, we found a package online to extract musical data from our xml files, but ran into problems with this package. We discussed whether to write our own script or try to fix the problems we were having with the provided package, but we decided that the benefits of that existing package outweighed the difficulties in working with it. Eventually, we were able to solve most of the errors that were occurring by modifying parts of the matlab scripts given and adding some additional features (such as fixing a bug with the way that lyrics were recorded), and we now have ~5000 usable text files that contain both the lyrics (in syllable format) and the corresponding notes (with pitch and duration data). After shifting the pitches to intervals, we will be done formatting the data. Among other things, using the given package prevented us from having to transpose the music to Cmaj and from having to parse the words into syllables ourselves.

We originally planned to have a website to showcase our project, but due to feedback from many people, we decided to put it aside and focus more on the actual NLP aspects of the project, which will be challenging enough. This also removes the need for an API that sings lyrics with a given melody.

In terms of picking our classification algorithm, we've decided to use an HMM, as this most closely fits our data. The notes will be the hidden states, and the outputs will be the syllables. We intend to start with a bigram model, and then extend this to trigrams. We would also like to incorporate note lengths as well (instead of solely pitch), so we plan to extend our HMM to a factorial HMM (ie. a dynamic Bayesian network) that has both note pitches and note lengths as the states, and syllables as the outputs.

