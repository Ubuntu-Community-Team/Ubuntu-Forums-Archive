---
title: "Installing Snack"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by HaroHaro on 2009-09-17
I downloaded snack2.2.10 from the snack website an I'm following the Unix installation on the README file. However when I'm trying to do the make command, it gets this error:

bhui004@bcli07:~/snack2.2.10/unix$ make
gcc -pipe -shared sound.o jkSound.o jkSoundEngine.o jkSoundEdit.o jkSoundFile.o g711.o jkAudIO_oss.o jkFormatMP3.o jkSoundProc.o ffa.o jkPitchCmd.o snackStubInit.o jkAudio.o jkMixer.o shape.o jkFilter.o jkSynthesis.o jkFilterIIR.o jkGetF0.o sigproc.o jkFormant.o sigproc2.o -lc  -L/home/ccp4dev/ccp4mg-rel-1-1/tcltk_new/lib -ltcl8.4 -o libsound.so 

/usr/bin/ld: cannot find -ltcl8.4
collect2: ld returned 1 exit status
make: *** [libsound.so] Error 1

Do you guys know how I can fix this?

---

### Post by Mitch9654 on 2009-09-17
Did you try Applications/Add Remove Programs(or something like that)?

mitch9654

---

### Post by HaroHaro on 2009-09-18
I can't use the add/remove programs or the synaptic manager because I don't have admin privileges (on a uni comp).

---

### Post by Mitch9654 on 2009-09-18
go to Apps/Accesories/Terminal and type in 

sudo apt-get install (your_program_name_here)
and type in the password(if you know it)

mitch9654

---

