---
title: "sound device not installing"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by koenig on 2007-03-25
IXP SB400 AC'97 Audio Controller

hey i just started using Ubuntu and i like it alot, however, i cant get the sound to work.
ubuntu recognizes the device but it doesnt work, so i think its just missing the driver.
i went to [www.alsa-project.org](www.alsa-project.org) and went through the instructions and downloaded the driver package (or what i thought it was because there was no direct link to the specific driver, i went to the ftp and downloaded the most recent tar.gz under /driver) and then followed the instructions.

> 
Make a directory to store the alsa source code in.

        cd /usr/src
        mkdir alsa
        cd alsa
        cp /downloads/alsa-* .

Now unzip and install the alsa-driver package

        bunzip2 alsa-driver-xxx
        tar -xf alsa-driver-xxx
        cd alsa-driver-xxx
        ./configure --with-cards=atiixp --with-sequencer=yes;make;make install


everything went fine until the last step
" ./configure  --with-cards=atiixp --with-sequencer=yes;make;make install "

at the end of the command two errors occur with file permissions

[COLOR="Red"]install: cannot create directory `/usr/include/sound': Permission denied
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
[/COLOR]

i type sudo before every command...so i dont understand

any help is greatly appreciatied (ive searched the forums and online, but im new so maybe im missing something)**[B]**[/B]

---

### Post by koenig on 2007-03-25
no sound for me =(
anyone?

---

### Post by koenig on 2007-03-26
bump

---

