---
title: "Errors with message bus daemon"
date: 2008-07-23
forum: General Help
---

### Post by Bruce M. on 2008-07-23
Hi Folks,

Well it seems I'm not alone. I know I brought this up before, maybe 6 months back, but there are a few of us experiencing the same type of problem at shut down. I didn't describe the problem as well as greendragonfire did so maybe that's why I never got an answer for a proper fix.

So far; greendragonfire, nat6138, vjkeito, agaudio, GavinZac, caleechee, bastos77, mailtwogopal and myself all have the same problem.

If you have any idea how to fix the errors at shut down that are quite nicely described in the thread started by greendragonfire in Absolute Beginners Talk: [message bus daemon]("http://ubuntuforums.org/showthread.php?t=686123") could you pop in there and give us some insight please.

That thread has obviously lost it's "0 response" status and may never see the light of day for something useful to stop the errors.

So if you're a Linux/Ubuntu guru and want to help at least the nine of us we'd be very pleased to see you.

I see that I don't even have the "daemon" package installed. Shouldn't that be installed by default?

From Synaptic Package Manager:
> daemon
turns other processes into daemons
There are many tasks that need to be performed to correctly set up a
daemon process. This can be tedious. Daemon performs these tasks for
other processes. This is useful for writing daemons in languages other
than C, C++ or Perl (e.g. /bin/sh, Java).

If you want to write daemons in languages that can link against C functions
(e.g. C, C++), see libslack which contains the core functionality of daemon.

Upstream URL: [http://www.libslack.org/daemon/](http://www.libslack.org/daemon/)

My Guru Status: Conceived last night, see you in 9 months. :lolflag:
So what do I know???

Have a nice day.
Bruce

---

### Post by djonepl on 2008-08-31
i get the same error while shuting down =|

---

### Post by pherber12 on 2008-09-18
me too

---

### Post by dilmah on 2008-09-24
I fixed this on my computer by changing the configuration of my network card in the Network Manager applet. I disabled roaming mode and just hard coded it to use DHCP. No more shut down errors!

---

### Post by Bartje on 2009-01-25
I've got the same problem, but it's weird :
I used Ubuntustudio, 8.04, no problem, no error message. I then upgraded to Intrepid, no problem either, at least not having the error message. I did have other problems, couldn't get my external usb soundcard working anymore, so decided to go back to 8.04. Reinstalling from scratch, using the same DVD that I used the first time installing 8.04 and there it was, the error message from the bus deamon.:-k:?:

---

