---
title: "Webcam upside down"
date: 2010-09-24
forum: Hardware
---

### Post by mncjr94 on 2010-09-24
Hi, I'm new to linux but i got most of my stuff in check on it.  The only problem is that when i log into skype my webcam is flipped upside down.  The hardware drivers says there are no drivers needed and this is really buggin me.  I have an asus laptop and this is a built in webcam.  I think its an [COLOR=Black]*ASUS USB2*.*0 UVC* VGA [I]WebCam.  Can anyone help me??

EDIT: I'm using Ubuntu 10.04
[/I][/COLOR]

---

### Post by SteveDee on 2010-09-24
Is it only upside down in Skype?

Try opening a terminal and typing: gstreamer-properties
...and run the video test. Is the video the right way up?

---

### Post by mncjr94 on 2010-09-24
> **SteveDee said:**
> Is it only upside down in Skype?

Try opening a terminal and typing: gstreamer-properties
...and run the video test. Is the video the right way up?

Ok iit's upside down in everything.....:confused:

---

### Post by SteveDee on 2010-09-24
I think the answer is here: [http://www2.warwick.ac.uk/services/its/servicessupport/deskside/linuxworkstationguide/faqsandtips/upsidedownwebcams/](http://www2.warwick.ac.uk/services/its/servicessupport/deskside/linuxworkstationguide/faqsandtips/upsidedownwebcams/)

---

### Post by mncjr94 on 2010-09-24
> **SteveDee said:**
> I think the answer is here: [http://www2.warwick.ac.uk/services/its/servicessupport/deskside/linuxworkstationguide/faqsandtips/upsidedownwebcams/](http://www2.warwick.ac.uk/services/its/servicessupport/deskside/linuxworkstationguide/faqsandtips/upsidedownwebcams/)

I'll try that now:)

---

### Post by mncjr94 on 2010-09-24
Unfortunately i have no idea how to open tar.bz2 files....i have to download sumtin then i put in the commands in the terminal for the webcam to work.  Sorry that i don't know how to open these files i juss have issues cause im new to ubuntu.  Can anyone tell me how to open these files?

---

### Post by SteveDee on 2010-09-25
> **mncjr94 said:**
> Unfortunately i have no idea how to open tar.bz2 files....i have to download sumtin then i put in the commands in the terminal for the webcam to work.  Sorry that i don't know how to open these files i juss have issues cause im new to ubuntu.  Can anyone tell me how to open these files?

OK if you want to proceed, take a look at this article which explains file compression and how to decompress your file: [http://learn.clemsonlinux.org/wiki/File_Compression](http://learn.clemsonlinux.org/wiki/File_Compression)

Once you have done this there may be a help file to tell you what to do next.

Edit: You will probably also need this info:[http://learn.clemsonlinux.org/wiki/Compiling_programs](http://learn.clemsonlinux.org/wiki/Compiling_programs)

---

### Post by mncjr94 on 2010-10-31
no matter what i do i cant open the file you reccommended, i just dont know how and its killin me

---

### Post by ednella on 2011-09-20
> **SteveDee said:**
> I think the answer is here: [http://www2.warwick.ac.uk/services/its/servicessupport/deskside/linuxworkstationguide/faqsandtips/upsidedownwebcams/](http://www2.warwick.ac.uk/services/its/servicessupport/deskside/linuxworkstationguide/faqsandtips/upsidedownwebcams/)

Hello,
I've got the same problem. My ASUS K50IJ has a webcam in upside down (only running Skype, no problem with gmail videochat, or cheese).
I tried this: gstreamer-properties; and the test pass ok. But the problem still just with Skype.
I tried your link, but I do womething wrong because I receive de message "command not found"

What should I do?
Thank you very much

---

### Post by Elfy on 2011-09-20
Old thread closed.

---

