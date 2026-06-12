---
title: "midi devices and rosegarden, arrrrgh!"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by bigbang on 2007-01-12
OK, I'm being driven insane by trying to get my midi devises to work on rosegarden. this is what i have tried :

first i tried with my speakers, i got this: " Sequencer startup failed: MIDI subsystem has failed to initialize" and in beast i got a similar message when i tried to play midi 'stuff'.

now i tried a different approach i plugged in an old midi keyboard with a Yamaha cable (this worked on windows and so did the speakers). same result. i looked up the message and found this thread: 
[http://groups.google.co.uk/group/linux.debian.maint.kde/browse_thread/thread/2a1b272e233895f8/152f1beac9f12666?lnk=st&q=rosegarden+sequencer+startup+failed&rnum=1#152f1beac9f12666](http://groups.google.co.uk/group/linux.debian.maint.kde/browse_thread/thread/2a1b272e233895f8/152f1beac9f12666?lnk=st&q=rosegarden+sequencer+startup+failed&rnum=1#152f1beac9f12666)
so i tried "modprobe snd-seq-midi"  yey! i thought to my self as it loaded without giving me the error till it landed this on me:
"**System timer resolution is too low**
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information."
now it plays and the devises show up but without actual making any sound!

arrrrgh! that's it for one night. can anyone help me in simple plain English, assuming i know only what i told you? i would prefer to manage using my speakers.:confused:

---

### Post by bigbang on 2007-02-19
the answer was to install a new kernel (media kernel)

---

### Post by Phatfiddler on 2007-02-27
what exactly do you mean by the media kernel, because I am having the same issue.

---

### Post by gnowak on 2007-03-10
Yup, the same problem here too... can't figure out the solution.

---

### Post by gnowak on 2007-03-10
Hmm I found a solution....

Use the steps here: [http://www.cs.cornell.edu/~djm/ubuntu/#timidity]("http://www.cs.cornell.edu/~djm/ubuntu/#timidity") to run timidity.

Run as root:

apt-get install timidity timidity-interfaces-extra
modprobe snd-seq-device
modprobe snd-seq-midi
modprobe snd-seq-oss
modprobe snd-seq-midi-event
modprobe snd-seq
timidity -iA -B2,8 -Os1l -s 44100

While timidity is running in a terminal, run rosegarden as user.
Information to start these options automatically at startup is described in the above link.

I had to start rosegarden a couple of times, and at last it came up. Don't know why it had to be run so many times??

I get this information note though:

[I]System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.[/I]

The solution for this problem is apparently to wait for a special ubuntu media (Ubuntu Studios) distro coming later this year (2007).

Please let me know about other problems etc or a fix for the above information note.

Cheers.

---

