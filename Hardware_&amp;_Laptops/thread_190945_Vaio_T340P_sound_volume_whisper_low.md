---
title: "Vaio T340P sound volume whisper low"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by lenticular on 2006-06-06
Hi-
I'm running Dapper 2.6.15-23-386 on a Sony Vaio T340P laptop and having a problem with sound volume.  Any sound from the system (mp3, beep, whatever) comes out so quiet that I can only hear it on an external speaker with the volume turned up full.  I've installed the latest ALSA stuff, and alsaconf recognizes my Intel sound chip.  I've turned the speaker on full in BIOS as well.  If I use the desktop volume control, it goes from silent to barely audible.

My thought: this laptop has a mute button and + and - volume buttons on the front.  I don't think that they are recognized, and so system volume has defaulted to the lowest.

I've also tried to install sonyacpi to see if that will give me control, but no luck:
make
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/jr/Desktop/sony_acpi modules
make[1]: Entering directory `/lib/modules/2.6.15-23-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-23-386/build'
make: *** [default] Error 2

Any ideas or pointers would be much welcomed.
Thanks,
  John

---

### Post by lenticular on 2007-03-17
I solved this a while back with some digging in the forums, but just to be complete...

I needed to run alsamixer and turn the external amp setting to off.

-John

---

