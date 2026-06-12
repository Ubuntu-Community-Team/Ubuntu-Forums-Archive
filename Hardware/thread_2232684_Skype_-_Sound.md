---
title: "Skype - Sound"
date: 2014-07-03
forum: Hardware
---

### Post by lolsi11 on 2014-07-03
Hello, sorry for my bad english but I try my best to describe problem I got in to.
I install ubuntu 14.04 today and I realized that skype sound dosen't work way it should, all hardware that skype show is "virtual device".
Does anyone know how to solve that, mic and sound work on other programs. At least cam work

---

### Post by xc3RnbFO8P on 2014-07-05
Sometimes when hardware isnt working I reinstall the kernel:
> sudo apt-get install --reinstall linux-image-$(uname -r)

---

### Post by miles6 on 2014-07-05
omg this worked thanks :D

---

### Post by enricofranceschi on 2014-08-03
same problem, but the solution don't work for me on lubuntu14.04 (32 and 64bit), other suggestions

---

### Post by felly2 on 2014-08-03
Try to Uninstall it and Install again...then observe changes

---

### Post by enricofranceschi on 2014-08-04
no changes

I have tried:

   sudo apt-get purge skype*
 sudo apt-get clean
 sudo apt-get autoclean
 sudo apt-get autoremove

I deleted .Skype folder
and reinstalled
but nothing to do





   I partially solved by installing pavucontrol,but brings pulseaudio that I don't like, e microphone don't work e only selectable option PulseAudio server (local)


Other tips?

---

### Post by Light-kun on 2014-10-08
Same problem (as enricofranceschi has) here on fresh Linux Mint 17 Qiana. Tried few fixes including kernel reinstall - but still have only virtual devices in skype preferences.

Upd.: I'va managed to get it working after trying to start pavucontrol and getting "no pulseaudio server available". Found no pulse process, started it explicitly by running '''pulseaudio''' and finally - skype works flawlessly!
In startup comands i've found this one '''start-pulseaudio-x11'''. Manual run outputted only errors, so I've changed this broken command to '''pulseaudio'''.

---

### Post by svenmeier on 2014-12-16
Installing the 32bit pulseaudio library helped here on 14.10.:

    sudo apt-get install libpulse0:i386

---

### Post by osk2 on 2015-02-09
> **svenmeier said:**
> Installing the 32bit pulseaudio library helped here on 14.10.:

    sudo apt-get install libpulse0:i386

This worked for me on Ubuntu 14.04 with Skype 4.3.0.37

---

### Post by sandys1 on 2015-02-13
> **svenmeier said:**
> Installing the 32bit pulseaudio library helped here on 14.10.:

    sudo apt-get install libpulse0:i386


works for me too . Thanks!!!

---

### Post by djbacon on 2015-06-02
> **svenmeier said:**
> Installing the 32bit pulseaudio library helped here on 14.10.:

    sudo apt-get install libpulse0:i386

You're a saviour :) 
It worked for me on Ubuntu 15.04 (64bit)
Thank you VERY VERY much :)

---

### Post by joel37 on 2015-07-13
> **svenmeier said:**
> Installing the 32bit pulseaudio library helped here on 14.10.:

    sudo apt-get install libpulse0:i386

Had the same issuee  and this worked pefectly, Thank you

---

### Post by tedy58 on 2015-09-15
> **svenmeier said:**
> Installing the 32bit pulseaudio library helped here on 14.04.:

    sudo apt-get install libpulse0:i386

This work for me too on Ubuntu 14.04.3

---

### Post by vassmarc on 2015-11-04
> **svenmeier said:**
> Installing the 32bit pulseaudio library helped here on 14.10.:

    sudo apt-get install libpulse0:i386

it also works for me in Ubuntu 14.04.3 LTS. Thank you very much.

---

### Post by stefan-kalb on 2015-11-05
> **svenmeier said:**
> Installing the 32bit pulseaudio library helped here on 14.10.:

    sudo apt-get install libpulse0:i386

This does still the trick for 15.10

---

### Post by dharmendra.bhargav on 2016-02-26
> **svenmeier said:**
> Installing the 32bit pulseaudio library helped here on 14.10.:

    sudo apt-get install libpulse0:i386

Worked for me too on Ubuntu 15.04 for Skype 4..
Thanks a lot :)

---

### Post by oldos2er on 2016-02-26
Old thread closed.

---

