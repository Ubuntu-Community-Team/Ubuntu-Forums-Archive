---
title: "Bluetooth mouse connection problem"
date: 2010-04-14
forum: Hardware
---

### Post by mikeee99 on 2010-04-14
I have a                            logitech bluetooth travel mouse (M-RBB93. I am using Ubuntu Release 9.10 (karmic) kernal Linux 2.6.31-20-generic GNOME 2.281.1. 

 When I try to connect it using the "Set Up New Device..." button under the bluetooth icon it finds the mouse when it searches for new devices, but when I try to connect it it tells me: "Setting up 'Bluetooth Travel Mouse' failed". 

Also, whenever I move the mouse I get the following message:

**"Grant access to '00001124-0000-1000-8000-00805f9b34fb'**
Device " Bluetooth Travel Mouse" (00:07:61:49:F5:39)
wants access to the service
'00001124-0000-1000-8000-00805f9b34fb'.

[] Always grant access
Reject Grant"

Here is a screen shot of the error:

[IMG]http://i97.photobucket.com/albums/l229/Mikeee79/Mouse_trouble_Screenshot.png[/IMG]


      No matter how many times I grant access or whether or not I check the "always grant access" box, it just keeps asking me the same thing whenever I move the mouse and the bluetooth detects it.

I am sure it is not the bluetooth antenna, which is a Kensington Bluetooth USB Adapter 2.0 Model# K33348b, because I have connected other blue tooth devices such as my phone and a keyboard.

I have searched these forums and it seems to work fine for everyone else. If someone could help me out that would be great, also I am new, so if you need more information, please let me know what I need to provide and, if possible, where I can find it.

Thanks Everybody!

---

### Post by eusouumdiospiro on 2010-04-15
Hi!

I have a Toshiba NB200 netbook and a Logitech M555b bluetooth mouse, and the symptoms are exactly the same.

Some time ago I managed to solve it, but in the meanwhile I reinstalled ubuntu (in both situations vesion 9.10, although this time I have the netbook remix) and I can't remember anymore where I found the solution.

I'll keep looking and leave here an update if I find it.

---

### Post by eusouumdiospiro on 2010-05-04
Well, this was eventually solved by simply using the "Connect" button in the mouse.
After doing it, the pairing was successful.
I guess I should have thought about that before searching for solutions in the forums. :)

---

### Post by ravensqu on 2010-08-05
I am having the same problem with a Logitech MX Revolution Mouse that I have been using for a long time on a Windows PC. I just made the switch to Ubuntu and am very new to it, no matter how much I play with the connect button, it keeps refusing access to the service. Please Help.

---

### Post by ingeva on 2010-08-06
> **ravensqu said:**
> I am having the same problem with a Logitech MX Revolution Mouse 
If you are using Ubuntu 10.04, Lucid, you should be aware that there's a general problem with mouse and keyboard connected via bluetooth.
My computer is a Dell Vostro 400 which supports the bluetooth from the BIOS level, and there are no problems with Windows or earlier Ubuntu versions, except I had to uninstall all bluetooth managers.
With 10.04, however, there's no connection even with the server version, before the desktop software (gnome) is loaded.

Serious problem. Can't use 10.04. I wonder if I'll be able to use any later versions....

---

### Post by ravensqu on 2010-08-09
Crap that really sucks. Lucid is the best distro I have found so far, this is the only thing I have found that doesn't work. I was speaking to a friend about the problem and he was saying there was some way to adjust the auto-paring of the mouse to all 1's or all 0's. Was thinking of an onboard bluetooth connection not through the adapter? I'm still very new to Ubuntu so I don't know much about this. Thanks for all your help.

---

### Post by eusouumdiospiro on 2010-08-10
> **ravensqu said:**
> I am having the same problem with a Logitech MX Revolution Mouse that I have been using for a long time on a Windows PC. I just made the switch to Ubuntu and am very new to it, no matter how much I play with the connect button, it keeps refusing access to the service. Please Help.

I was only able to solve things with the "connect" button after seeing that dialog with "Grant access to 'DEVICE ADDRESS'".
After installing ubuntu (either 9.10 or 10.04), first I had to follow the instructions I found in this thread ([http://ubuntuforums.org/showthread.php?t=1215665&page=12]("http://ubuntuforums.org/showthread.php?t=1215665&page=12")) (the post from jeroenimo on page 12). Before that the bluetooth adapter wasn't even recognized.

Hope it helps.

---

### Post by ravensqu on 2010-08-11
Im able to follow the instructions up to the point where I build omnibook-source. But when the progress bar hits 23% I get this error in the module-assistant:

```
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.32-24-generic-pae/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.32-24-generic-pae/g  ;s/#KVERS#/2.6.32-24-generic-pae/g ; s/_KVERS_/2.6.32-24-generic-pae/g ;  s/##KDREV##/2.6.32-24.39/g ; s/#KDREV#/2.6.32-24.39/g ;  s/_KDREV_/2.6.32-24.39/g  ' < $templ > ${templ%.modules.in}; \
  done
[ ! -f Makefile ] || /usr/bin/make KSRC=/usr/src/linux-headers-2.6.32-24-generic-pae clean
make[1]: Entering directory `/usr/src/modules/omnibook'
make -C /usr/src/linux-headers-2.6.32-24-generic-pae M=/usr/src/modules/omnibook clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
  CLEAN   /usr/src/modules/omnibook/.tmp_versions
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
rm -f -r *~ "#*#" .swp
rm -f -r debian/omnibook-source *-stamp
rm -f -r Module.symvers Modules.symvers
make[1]: Leaving directory `/usr/src/modules/omnibook'
dh_clean
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/omnibook'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.32-24-generic-pae/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.32-24-generic-pae/g  ;s/#KVERS#/2.6.32-24-generic-pae/g ; s/_KVERS_/2.6.32-24-generic-pae/g ;  s/##KDREV##/2.6.32-24.39/g ; s/#KDREV#/2.6.32-24.39/g ;  s/_KDREV_/2.6.32-24.39/g  ' < $templ > ${templ%.modules.in}; \
  done
[ ! -f Makefile ] || /usr/bin/make KSRC=/usr/src/linux-headers-2.6.32-24-generic-pae clean
make[2]: Entering directory `/usr/src/modules/omnibook'
make -C /usr/src/linux-headers-2.6.32-24-generic-pae M=/usr/src/modules/omnibook clean
make[3]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
rm -f -r *~ "#*#" .swp
rm -f -r debian/omnibook-source *-stamp
rm -f -r Module.symvers Modules.symvers
make[2]: Leaving directory `/usr/src/modules/omnibook'
dh_clean
sed -i -e 's/_STEM_/linux/g' debian/control
dh_testroot
dh_clean -k
dh_installdirs lib/modules/2.6.32-24-generic-pae/extra
# Build the module
/usr/bin/make KSRC=/usr/src/linux-headers-2.6.32-24-generic-pae KVERS=2.6.32-24-generic-pae
make[2]: Entering directory `/usr/src/modules/omnibook'
/usr/bin/make -C /usr/src/linux-headers-2.6.32-24-generic-pae SUBDIRS=/usr/src/modules/omnibook modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
  CC [M]  /usr/src/modules/omnibook/init.o
/usr/src/modules/omnibook/init.c: In function ‘omnibook_init’:
/usr/src/modules/omnibook/init.c:294: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[4]: *** [/usr/src/modules/omnibook/init.o] Error 1
make[3]: *** [_module_/usr/src/modules/omnibook] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
make[2]: *** [omnibook.ko] Error 2
make[2]: Leaving directory `/usr/src/modules/omnibook'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/omnibook'
make: *** [kdist_build] Error 2
```Does anyone have an idea how I can get this to build properly?

---

### Post by eusouumdiospiro on 2010-08-11
> **ravensqu said:**
> ]Does anyone have an idea how I can get this to build properly?

Go back to the previous step (check the init.c). If the line you commented is again uncommented, do it once more and then repeat the build command (the -O in the command is capital "o").

In case this was not the problem, make sure that there are no warnings in the previous steps (I remember at some point there were some dependencies missing, but I don't remember exactly where).

---

### Post by ravensqu on 2010-08-11
Thank you so much for the link and the tip. Finally it is all working. =D

---

