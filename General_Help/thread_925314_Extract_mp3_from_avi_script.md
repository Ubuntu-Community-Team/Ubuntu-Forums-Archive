---
title: "Extract mp3 from avi script"
date: 2008-09-20
forum: General Help
---

### Post by ThorX89 on 2008-09-20
Hi. The command 
```
mplayer -dumpaudio $INPUT -dumpfile $OUTPUT
```
when applied on an *.avi $INPUT file will extract an mp3 file call $OUTPUT in a second.
If I wanna do this for all avi files in a directory so that the output file's name is the same as the input except for the extension, I can type this in the command line:
```
ls *.avi | while read INPUT; do mplayer -dumpaudio "$INPUT" -dumpfile "${INPUT/%.avi/.mp3}"; done

```
I notice there's a utility called nautilus actions that allows me to add an item in the right-mouse-click menu for all files of a given type.
Is there a way to set it up, so that there would be an item that would do this for all avi files selected?
 I guess it'll involve writing a script that would process the given file names and create the $INPUT and $OUTPUT variables, which it would subsequently feed to the abovementioned mplayer command.
But no idea how to do that, never written a script before?
Any hints, or links at least?

---

