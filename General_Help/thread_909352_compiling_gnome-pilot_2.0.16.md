---
title: "compiling gnome-pilot 2.0.16"
date: 2008-09-03
forum: General Help
---

### Post by dclement on 2008-09-03
Hi,

I'd like to try gnome-pilot 2.0.16 which seems to allow synchro. through bluetooth. There is no .deb file, so I downloaded and extracted the sources. After that... I am in trouble:

./configure gives me the following output:

  Configuration :

          gnome-vfs    : yes
          network sync : yes
          usb          : yes
          HAL/DBUS     : no
          gob          : no
          pilot-link   : 0.12.3

(however, the script terminates; at first it stopped complaining for missing packages. I think I have spotted and added them all right.)

What is that "HAL/DBUS : no"? (I do have "hal" and "dbus" packages on my system.)

If I try "make", here is what I get:

make  all-recursive
make[1]: entrant dans le répertoire « /home/daniel/Download/gnome-pilot-2.0.16 »
Making all in po
make[2]: entrant dans le répertoire « /home/daniel/Download/gnome-pilot-2.0.16/po »
file=`echo ar | sed 's,.*/,,'`.gmo \
      && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[2]: *** [ar.gmo] Erreur 127
make[2]: quittant le répertoire « /home/daniel/Download/gnome-pilot-2.0.16/po »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/daniel/Download/gnome-pilot-2.0.16 »
make: *** [all] Erreur 2

I do not understand all these errors! Can anyone help me?
Thanks in advance - best regards, Daniel

---

### Post by dclement on 2008-09-06
I reply to myself because I made some progresses with the help of a colleague who told me to install the gettext package.

It allowed "make" to complete, and then "make install".

I also installed gnome-pilot-conduits 2.0.16.

But, my gnome-pilot "about" box still says "2.0.15".

However, I now have a "bluetooth" option under the device tab. Alas, it does not work: the bluetooth connection indeed takes place, but the the hotsync hangs or claims "the serial port is in use by another app."

My guess is that only the conduits are installed, and the main program is not. What else should I try?

TIA - regards, Daniel

---

