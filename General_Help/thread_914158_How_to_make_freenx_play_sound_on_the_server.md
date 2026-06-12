---
title: "How to make freenx play sound on the server"
date: 2008-09-08
forum: General Help
---

### Post by Chris Musampa on 2008-09-08
Hi all, I've installed freenx server on my desktop machine and can login through the laptop.  I tried it because I thought it would be quicker than vnc for using amarok on the server.  Trouble is amarok reports that cant access the sound system.  I guess the problem is its trying (and failing) to forwar sound to the client.

Is there a way to make the server use it's normal (local) sound output?  Google only turned up results for problems with forwarding not working so I guess its an odd request.

Thanks in advance.

---

### Post by Chris Musampa on 2008-09-11
Bumpage.

---

### Post by phantom_ on 2010-01-07
answer comes quite late! ;)

i just got the same intention with you. that is, i would like to access the system with an efficient remote software, play music and get the sound from the server; not my client.

i am running 9.10 karmic koala with GNOME as desktop manager. my freenx client is a Windows XP workstation.

i failed to get sound neither from the server nor from the client computer. i tried amarok & rhythmbox. however, system reported no sound hardware at all. i also checked *pulseaudio device chooser*. sound hardware did not exist when logged in thru freenx. _however, everything was functional thru TTY logins_.

**then i found this thread; [http://ubuntuforums.org/showthread.php?t=1099244](http://ubuntuforums.org/showthread.php?t=1099244)**

after reading the above, i login over TTY terminal and start GNOME. then i logout, and login thru freenx. sound subsystem works. it continues working if you logout then login thru freenx.

it is obvious that freenx software has some bugs after the upgrade of software mixer from ESD server to PulseAudio at Ubuntu. there is a compatibility package for ESD dependent audio software (installed in my system), but it does not solve anything.

please note that the above sequence is not a solution but just a workaround. sound subsystem works at the server, however; sound is not streamed to freenx client, even though *enable multimedia *checkbox is ticked at the client.

after running VNC for a long time, i find freenx much more efficient. that is because **freenx is not a remote desktop software but an X server/client system**.

i hope all the above helps you and many other users trying the solve the sound problem with freenx deployment!

---

### Post by juancarlospaco on 2010-01-07
You need to redirect sound into a port and then connect to that port,
you can do the same with mic, and is a howto here on the forum, good luck
:)

---

### Post by djieno on 2013-03-26
hi juancarlospaco,

Could you be so kind to elaborate on that? I found this link below but *didn't* do the trick for me

[http://askubuntu.com/questions/171431/freenx-sound-fw]("http://askubuntu.com/questions/171431/freenx-sound-fw")

In the freenx session open a terminal and paste below.
> pacmd load-module module-tunnel-sink server=[YOUR_CLIENT_IP]

Would be great to have this working!

djie

---

### Post by oldos2er on 2013-03-26
Old thread closed, please start a new thread.

---

