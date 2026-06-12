---
title: "Cannot boot from Live CD"
date: 2009-12-28
forum: Hardware
---

### Post by sauma on 2009-12-28
Here's my problem:

I've got Ubuntu 9.1 and Windows 7 RC Build 7100 dual booting. They're usable, but I rarely venture over to Windows because they don't get along that well, they can't really share music/picture/etc. I bought a real copy of W7 (since the RC won't last too much longer)and was planning on starting over with a much cleaner, happier installation of the two. I downloaded the ISOs and realized I couldn't burn them. I used another computer to burn and the computer in question won't read either of them. I can't boot from the disc (or a usb drive, tried that too). The DVD drive can play audio CDs and movie DVDs just fine. I've spent hours on the phone with Gateway and they really have not helped at all.

Help?
Intel E5200 64 bit
DX4800-05e
NVIDIA GeF 9200
HL-DT-ST DVDRAM GH15F SCSI 

What other information might you need to diagnose a problem?

p.s. - I tried the discs and usb on the other computer that they work just fine.

---

### Post by sauma on 2009-12-28
Also, I have all my important things backed up. I'm just afraid that if I wipe everything, I won't be able to boot from the discs. I got the Windows 7 student upgrade for $30, is it possible to use this with a fresh install or does it have to be coming from an older version of Windows?

---

### Post by SecretCode on 2009-12-29
If you boot the existing windows or ubuntu, can you see files on the CD you've burned? If not I can only assume your cd drive is damaged and can't read data.

If you can read the CD but not boot, it's probably a BIOS option. At power on you should see a BIOS screen with a key - could be anything, Esc, Del, F2, F9, F12 - to change the boot order/boot menu.

---

### Post by sauma on 2009-12-29
That's the confusing part. I can read other discs, just not the ISOs that I burned (again, they did work on another computer). In 9.10 the drive disappears for a bit and in W7 explorer usually freezes and restarts. Neither can see anything on the disc. It makes a strange thudding noise in the drive.

---

### Post by SecretCode on 2009-12-29
The only thing that occurs to me is to burn the image again at the lowest possible speed.

---

### Post by sauma on 2010-01-01
Well that didn't really help anything. Can anyone think of why a drive would all of a sudden stop reading burned discs? Now that I think of it...it worked up until I installed linux a while ago. It there some sort of driver issue I ignored up until now?

---

### Post by viper250 on 2010-01-01
Did you use an iso burner program? many people try to use windows to burn an iso and then find out it fails!
 download and install infra recorder! It is a free iso burning utility program that works quite well.
 2nd some newer optical drives in newer notebooks have sata a interface and may not be able to read older distros 
If this is the case then you will need to download and use 64 bit distros.

---

### Post by sauma on 2010-01-01
I used imgburn. I tried again at the lowest speed using infra recorder. The disc shows up! but, alas, it is seen as blank. I'd call that a step in the right direction though!

---

### Post by sauma on 2010-01-04
Any help?

---

### Post by sauma on 2010-01-28
With a bit of luck, a Canonical-born live disk, and upgrade Windows 7 disc, I managed to wipe my hard drive, portion out my hard drive into 3 (+swap) nice, neat spaces. One for Ubuntu, one for Windows and one huge one as a shared library space. It's working beautifully and I'm in the process of moving all my necessary files back. 

Thank you?

---

