---
title: "Arduino not running (Ubuntu 9.04 )"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by buteo_12701 on 2009-07-14
Naturally I am a newb to Ubuntu and have been trying to get Arduino to run on my newly found OS. I cant seem to get arduino to run after fully following(atleast i think i did) The installation instructions. I Tried running it through the terminal and came up with the following info:

java.lang.UnsatisfiedLinkError: /home/bruce/Desktop/arduino-0016/lib/librxtxSerial.so: /home/bruce/Desktop/arduino-0016/lib/librxtxSerial.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch) thrown while loading gnu.io.RXTXCommDriver
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/bruce/Desktop/arduino-0016/lib/librxtxSerial.so: /home/bruce/Desktop/arduino-0016/lib/librxtxSerial.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1778)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1703)
    at java.lang.Runtime.loadLibrary0(Runtime.java:823)
    at java.lang.System.loadLibrary(System.java:1030)
    at gnu.io.CommPortIdentifier.<clinit>(CommPortIdentifier.java:83)
    at processing.app.Editor.populateSerialMenu(Editor.java:915)
    at processing.app.Editor.buildToolsMenu(Editor.java:812)
    at processing.app.Editor.<init>(Editor.java:190)
    at processing.app.Base.<init>(Base.java:137)
    at processing.app.Base.main(Base.java:104)

Any help would be greatly appreciated. Im sure im making a mistake here somewhere. I would imagine i made sometype of mistake with java.

-B

---

### Post by buteo_12701 on 2009-07-14
bump

---

### Post by RoestVrijStaal on 2009-07-14
Probably you haven't install java runtime enviroment.
You could install the "official" Sun version via "Add/Remove..." if you set "Add/Remove" to "Display All possible Programs" and search for "java".

BTW: have you checked this pages @the site of Arduino? :)
[http://www.arduino.cc/playground/Learning/Linux](http://www.arduino.cc/playground/Learning/Linux)
[http://www.arduino.cc/playground/Linux/Ubuntu](http://www.arduino.cc/playground/Linux/Ubuntu)

Tell us if this helps or not :)

---

### Post by buteo_12701 on 2009-07-14
Thanks for the reply. I have sun java installed i tried reinstalling it. I used those two pages for my installation. Basically when i go to run arduino...i hit run and it asks me what folder i should use for the sketches...than after i choose it just doesnt do anything at all.

---

### Post by buteo_12701 on 2009-07-14
perhaps avrdude is installed unproperly?

---

### Post by RoestVrijStaal on 2009-07-15
It could be possible. You could try to reinstall avrdude and try arduino again.

It seems also that the arduino wants to speak to hardware, in most of those cases it must run as root.
To try to run Arduino as root , run this in terminal: 
```
gksudo arduino
```

---

### Post by dro0g on 2009-07-15
I've been running Arduino 0016 on Jaunty and it's been OK (once I worked through the Java issues)

From the error message you posted, I'm wondering if you're running into a 32/64 bit issue:
> /home/bruce/Desktop/arduino-0016/lib/librxtxSerial.so: **wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)** thrown while loading gnu.io.RXTXCommDriver

Are you running Jaunty 64-bit or 32?

---

### Post by buteo_12701 on 2009-07-15
im runnin the 64 bit...:)

---

### Post by dro0g on 2009-07-15
> **buteo_12701 said:**
> im runnin the 64 bit...:)

 I have not tested this myself because I don't have access to a 64-bit install, /me shakes old-man-fist "32-bits should be enough for anyone!" :) but see if these instructions help at all (in particular the 32-bit compatibility libraries)

[http://myy.helia.fi/~karte/arduino_editor_on_64_bit_ubuntu_gutsy.html](http://myy.helia.fi/~karte/arduino_editor_on_64_bit_ubuntu_gutsy.html)

---

### Post by spike the jackal on 2009-08-31
AH! I've seen this before!
Check out the bit on 64-bit midway down [this]("http://www.arduino.cc/playground/Learning/Linux") link.

---

