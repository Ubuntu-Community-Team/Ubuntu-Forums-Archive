---
title: "Installing minimal desktop version with no X (GUI)"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by tomsimmons on 2009-10-21
Evening All

I wonder if anyone could shed any light on performing a fairly minimal install?

Pretty much all I think I'll need is...

Networking
Sound
Bash
Java
Text Editor
Command line WAV record and play back.

The hardware is a EPIC MII 6000 with 512MB memory and a 4GB CF through an adapter in the IDE, and a CD Drive.

Thanks

Tom

---

### Post by compiledkernel on 2009-10-21
[http://gwos.org/udsf/doku.php/script:minimal:automated](http://gwos.org/udsf/doku.php/script:minimal:automated)

Included a little script, that should suit you just fine.

---

### Post by tomsimmons on 2009-10-21
> **compiledkernel said:**
> [http://gwos.org/udsf/doku.php/script:minimal:automated](http://gwos.org/udsf/doku.php/script:minimal:automated)

Included a little script, that should suit you just fine.

Blimey - now that's what I call a quick reply!

Thanks a lot.

Now at the risk of sounding a complete plonker, I have to confess I'm new to Linux, I have been using and configuring a GUI version after a plain install from the 8.10 CD, but how I use your script I'm not sure?

I've found the Minimal CD, but how would I use your script with it?


Thanks

Tom


PS 
I know that getting involved with this isn't ideal for a new start, but this is actually for a dedicated machine that I'll be controlling through commands sent via the Serial port and handled by either Bash or a Java program.

---

### Post by compiledkernel on 2009-10-21
You do the minimal install proper, then use the script (modified to your liking) to do the install the rest of the way. 

I believe when the minimal installer boots, you need to tell it to do a CLI install only.

---

### Post by tomsimmons on 2009-10-21
> **compiledkernel said:**
> You do the minimal install proper, then use the script (modified to your liking) to do the install the rest of the way. 

I believe when the minimal installer boots, you need to tell it to do a CLI install only.

OK.

Yes I'd seen that when it boots you type cli to get it going.  I was planning on using unetbootin to try it tonight, then realised I'd left my stinking USB stick at work.  (Burning a CD for a 12MB ISO is criminal :P)

I'll give it a shot tomorrow.


Tom

---

### Post by Sylslay on 2009-10-21
How use the script?
Copy/past text from [http://gwos.org/udsf/doku.php/script:minimal:automated](http://gwos.org/udsf/doku.php/script:minimal:automated),
save in file say "newscript"
channge chmod , or just porperty of file and tick permission "allow executeing file as program"

than run scrpit in terminal: 2 ways:

# bash newscript
or
# ./newscript 

And u may prepare Yours usb stick with UNetbootin,
to rework any disto.iso and write it into flashusb and copy newscript file togethet with minimal linux distro , so can use script after when setup internetconnection. but before run script, check is network is ok,
ping -c3 ubuntu.com

---

### Post by tomsimmons on 2009-11-20
OK, well I spent some time working on the other part of the project, the microcontroller that will be speaking RS232 to the Linux box to control it.  Wasn't helped when I was sold a dodgy serial cable!

In the time since I started this thread 9.10 has been released, so I download the mini.iso shoved it on the USB stick booted and now I've seen the start screen I'm not sure what I should be doing.

Should I take Default, or Command-line expert install, or hit tab and type cli?

I've had a look around on Google, a lot of the info I talks of a start screen like if you'd booted from the normal install CD, then seem to be hit tab and type cli.


Thanks

Tom

---

### Post by tomsimmons on 2009-11-21
> **tomsimmons said:**
> In the time since I started this thread 9.10 has been released, so I download the mini.iso shoved it on the USB stick booted and now I've seen the start screen I'm not sure what I should be doing.

Should I take Default, or Command-line expert install, or hit tab and type cli?

OK, think I've sussed it, hit TAB, typed cli and it seems to have worked.

I now have a question about a sound recorder/play back app.  I'm guessing that sound recorder you get when you install full Ubuntu with X is maybe the same as sound-recorder I hear of as a CLI app, just with a GUI front end?

If so I'm thinking I'll need apt get to get, but how do I find out the package name?


Tom

---

