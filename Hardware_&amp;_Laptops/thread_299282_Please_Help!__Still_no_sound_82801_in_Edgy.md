---
title: "Please Help!  Still no sound 82801 in Edgy"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by wylie348 on 2006-10-23
This is definitely a problem, and the 'solution' listed in the buntu bugs forum does not work for me.

Someone needs to come up with a fix (new kernel?) or possibly a how to that includes this problem where sound comes through headphone jack, but not internal speakers...

Thanks in advance all of you hardware/buntu gurus...
](*,)

---

### Post by edu65 on 2006-10-28
This is most strange. I had the same problem after going through the usual updates and switching to the 686 kernel in order to get SMP support.

I rebooted using the 386 kernel and got sound from the built-in speakers (just like
after a fresh install).

Now the strange part... booting back to the 686 kernel has made the speakers work again!  

Sorry if this does not help anyone. I just wanted to share my experience...

Using Dapper with a 2.6.15-27 kernel (HDA Intel / alsa mixer) on a Dell Inspiron 6400.


> **wylie348 said:**
> This is definitely a problem, and the 'solution' listed in the buntu bugs forum does not work for me.

Someone needs to come up with a fix (new kernel?) or possibly a how to that includes this problem where sound comes through headphone jack, but not internal speakers...

Thanks in advance all of you hardware/buntu gurus...
](*,)

---

### Post by wylie348 on 2006-11-13
Well after a month of trying I simply do not know where to go for help.  With an Intel 82801 sound card, I get sound out of my headphone jack, but nothing from the internal speakers.  There are no options in alsamixer for unmuting anything other than PCM and the master volume.
I have seen this problem in alot of places on the net - but no solutions.
I sure hope someone in the Buntu community can help!
Thanks in advance!
](*,)

---

### Post by wylie348 on 2006-11-14
Bump!

---

### Post by wylie348 on 2006-11-15
bump

---

### Post by John.Michael.Kane on 2006-11-16
You can double click on the speaker icon in your task bar.

This will bring up the Volume Control panel 

Click File Change device you should see intel ich (Alsa mixer)

Also under system pferences make sure under Sound Preferences match select ich if it does not.


You can unmute via terminal using the command use of sudo maybe needed

alsamixer

to store your settings run

alsactl store

---

### Post by wylie348 on 2006-11-17
Thanks, but did all of those things long ago and no change.  Sound works just fine from headphone jack - this appears to be a sense sort of thing.  There are no relevant choices listed in alsamixer to change.

There must be someone, somewhere, that can answer this problem?!
Thanks,

---

### Post by wylie348 on 2006-11-17
Re-install just stopped all sounds working, even under the new Alsa drivers.
Maybe someone else has a solution?

---

### Post by John.Michael.Kane on 2006-11-17
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
[http://ubuntuforums.org/showthread.php?t=87849&highlight=ICH6](http://ubuntuforums.org/showthread.php?t=87849&highlight=ICH6)

Other option

File a bug report [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)
Or
[https://launchpad.net/distros/ubuntu/+addticket](https://launchpad.net/distros/ubuntu/+addticket)

---

### Post by strabes on 2006-11-17
maybe your internal speakers are broken? Have you tried them in another OS?

---

### Post by wylie348 on 2006-11-19
Thanks, but speakers work just fine if windows is installed, but I am trying to move away from windoze.
:)

---

