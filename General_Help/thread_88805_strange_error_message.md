---
title: "strange error message"
date: 2005-11-11
forum: General Help
---

### Post by bionnaki on 2005-11-11
when I click on a .flac file, I get this error:

> The filename "01 - Schizophrenia.flac" indicates that this file is of type "FLAC audio". The contents of the file indicate that the file is of type "MP3 audio". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "MP3 audio", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 


does this mean that the file was transcoded from mp3 to flac? any ideas?

---

### Post by PaganHippie on 2005-11-11
It sounds as if the program you're trying to open the file with is trying to detect the encoding instead of simply relying on the file extension, which is rather sensible, but not always what you really want to happen.

Which program are you trying to open/play the file with? What happens if you ```
cp '01 - Schizophrenia.flac' '01 - Schizophrenia.mp3'
``` and then try to open/play the .mp3 file?

---

### Post by bionnaki on 2005-11-11
renaming the extension to .mp3 results in the file *not* playing. nothing happens - pretty much a dead file - no errors though.

---

### Post by bionnaki on 2005-11-11
also, when I attempt to convert the .flac to .ogg, all that results is total static...all other .flac files that are know to be *real flac* convert just fine...just not these.

---

