---
title: "Installed 2.6.38 Kernel &amp; mic stopped working - Ubuntu 10.10"
date: 2011-03-30
forum: Hardware
---

### Post by Noozybkk on 2011-03-30
Hi,

This morning I installed the 2.6.38-7-generic-pae kernel using the following files...

linux-headers-2.6.38-7_2.6.38-7.39~lucid1_all.deb
linux-headers-2.6.38-7-generic-pae_2.6.38-7.39~lucid1_i386.deb
linux-image-2.6.38-7-generic-pae_2.6.38-7.39~lucid1_i386.deb

The performance improvement is notable and everything is working perfectly except for the mic.

Can someone suggest what else I might need to do or install?

The computer is a Lenovo G550

The OS is x32 Ubuntu 10.10 (hence the need for the pae kernel since I have 4GB of memory)

I've searched already for a solution and I've found some stuff pertaining to x64 and ALSA, but nothing really that helps me.

---

### Post by DoctorBho on 2011-03-30
Unfortunately I have to say I have the same problem here - 64 bit 10.04 though.

There were bug reports about this issue concerning Natty, and they seem to be marked solved, so I&#8217;m wondering whether updating alsa is the way to go?

Or rolling back to the kernel without the "wonder patch" :-(

---

### Post by Noozybkk on 2011-03-30
I have another Lenovo, same spec that I haven't updated yet. I'm gonna keep it as is for now and just use it for Skype.

I'm not gonna roll back the Kernel on the problem machine just yet - at least until I've played with it some more.

---

### Post by DoctorBho on 2011-03-31
I am also loathe to give up "the patch that does wonders"!

I also have a lenovo s10 ideapad which I have updated (32 bit), and the microphone still works!

Curiously, in alsamixer on the working netbook, the microphone volume is set to zero and the boost is on.

Also, on my 64-bit desktop, the voice recorder is working, so I think it is just a pulse problem.

I have some ideas to test tonight... first alsamixer, then force recognition in /etc/pulse/default.p.

I’ll let you know if anything works!

---

### Post by DoctorBho on 2011-03-31
Good news!

With 2.6.38, lucid is not happy to recognise three inputs. It only takes two, defaulting to the front and line-in, so here&#8217;s what I did:

Open alsamixer (from the terminal).

Press F4 to get the capture devices.

Changed the input sources to rear and then front mike. (Initially I did both rear, where I discovered it worked!)

Turned up the volume for both, and the boost to 33.

Et voila! Skype worked.

BUT when I ran pulse volume editor, the settings defaulted back and I lost sound. So I had to set it again. I&#8217;m not touching it again...

Okay, it&#8217;s a hack, not a fix, but it DID work for me!

I hope this helps!

---

### Post by Noozybkk on 2011-03-31
Great. Will try that tonight although I have made things worse in the meantime. Today I tried to upgrade to ALSA 1.0.24 - the drivers and libs compiled but the utils failed to compile. Now I have no mic AND no sound!

---

### Post by DoctorBho on 2011-03-31
I hope you get it set up right again.

I am always nervous about the sort of "since you updated one  package, update another..." type fix. In my experience it often leads to an interminable sequence of updates and breakages - although I did update ALSA on an HTPC I built to get the HDMI working in XBMC (ALSA update script, since abandoned and then picked up by someone else - [http://ubuntuforums.org/showthread.php?p=10429842]("http://ubuntuforums.org/showthread.php?p=10429842")).

I find that a lot of times really complicated solutions are being described when often there is a much simpler solution a few clicks away - but not necessarily obvious.

Look on the bright side! Natty&#8217;s not far away - you could take the opportunity to reinstall and upgrade!

---

### Post by Yellow Pasque on 2011-03-31
> **Noozybkk said:**
> Great. Will try that tonight although I have made things worse in the meantime. Today I tried to upgrade to ALSA 1.0.24 - the drivers and libs compiled but the utils failed to compile. Now I have no mic AND no sound!
I would be interested in logs of that. ;)

---

### Post by Noozybkk on 2011-04-01
I went a bit crazy. I decided to upgrade to 11.04 using update-manager -d just to see what happened.

Everything started working straight away...however I have to say - I absolutely hate Unity and there doesn't seem to be any way of switching to Gnome Shell.

---

### Post by DoctorBho on 2011-04-01
Not even from the login screen? Or by adding Gnome from Synaptic?

I was under the impression that Gnome 2.3 would continue to be available and Shell was not quite ready yet.

I currently have Gnome, LXDE and ratpoison running. I won’t be happy if I am expected to switch to Unity - I already gave up on Netbook remix when I realised that I was stuck with all those "social" icons on the top panel!

---

### Post by Noozybkk on 2011-04-01
From what I've found on the net there was a way to change the shell at login, but apparently it got broken a few a weeks ago...there was nothing at all available on the login screen I got except the shutdown menu.

I think Mark Shuttleworth needs to sort out his gripe with Gnome or Ubuntu will lose a lot of popularity.

In order to keep this thread on track, I've installed Mint 10 now and am just tweaking it. I will do the 2.6.38 Kernel install tonight. If the mic breaks, I will try your hack and report back.

---

### Post by Noozybkk on 2011-04-02
Just installed 2.6.38.8 on the Mint machine. Mic stopped working so I did what you suggested with alsamixer. Worked. No problems with pulse.

Did exactly the same thing on the other Ubuntu machine. Same results.

It's all good once more. Thanks for your help.

---

### Post by krishna.988 on 2011-04-06
> **Noozybkk said:**
> Just installed 2.6.38.8 on the Mint machine. Mic stopped working so I did what you suggested with alsamixer. Worked. No problems with pulse.

Did exactly the same thing on the other Ubuntu machine. Same results.

It's all good once more. Thanks for your help.


Just curious what made you install an unsupported kernel in maverick??

---

