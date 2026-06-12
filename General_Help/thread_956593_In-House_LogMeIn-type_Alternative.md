---
title: "In-House LogMeIn-type Alternative?"
date: 2008-10-23
forum: General Help
---

### Post by ocr14a on 2008-10-23
Hi guys. 
Sorry, I wasn't sure where to post this question. 

Do any of you know if there is something like LogMeIn that can be installed and managed on the LAN (i.e. instead of having everything based with the LogMeIn folks)?

I really like LogMeIn and other similar services, but I'd like something that is all-us - the entire system runs on our server (maybe soemthing running on an Ubuntu VM within my ESX Server that provides the same kind of functionality).

Of course, I know it would only be accessible from my LAN, unless I exposed it to the outside world, but that's fine. I mainly want this to help with desktop support while I'm here at work anyway (and if I need to, I can just VPN in here, log onto my IT-Support workstation and use it from there). 

Any ideas?

steven

---

### Post by ocr14a on 2008-10-24
Any ideas at all?

---

### Post by cashmoney on 2008-10-24
Look at setting up VNC or Remote Desktop,  If you like the cli install SSH server-  But with the above you'll need to make sure you pass ports on your firewall and have a strong password.

---

### Post by ww711 on 2008-10-24
vnc would be the way to go for a simple internal LAN, e.g. real, tight and ultra vnc client

If the machine you use daily is linux ubuntu based, you can use the remote desktop application in ubuntu to rdp/vnc into the other machines depending if they are Windows or Linux based.

---

### Post by ww711 on 2008-10-24
There's a firefox plugin for logmein too.

[https://secure.logmein.com/connect_mozilla.asp?dothis=install](https://secure.logmein.com/connect_mozilla.asp?dothis=install)

---

### Post by ocr14a on 2008-10-24
Thanks...

Ok, I've used VNC before (actually, started with it in the early days, almost a decade ago), but I like the fact that with LogMeIn (and similar services), it's all there, ready to go, and all in one [fairly easy to use] interface.

I mean, I have all of my computers in their groups and all that. I also like the fact that it (LogMeIn) has the unchangeable warning message box on the *watched* end. - not a big deal, but nice.

So, is LogMeIn just a fancied up implementation of VNC? 
I thought it was their own thing for some reason. 

Is there a flavor of VNC out there that is secure, free and works like this (the all in one place interface, etc)?

p.s. Remote Desktop won't work, because I don't want to simply log in, I want to see what they see and be able to help them with it remotely. 

I do you Remote Desktop connections all the time, but that's when it's just me logging in to work on stuff by my self.

---

### Post by Chris Musampa on 2008-10-24
I installed x11vnc on my desktop machine, and use krdc to view it from the laptop, it does as I think you want, ie view/control the existing session rather than starting a new one.

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

---

### Post by ocr14a on 2008-10-24
> **Chris Musampa said:**
> I installed x11vnc on my desktop machine, and use krdc to view it from the laptop, it does as I think you want, ie view/control the existing session rather than starting a new one.

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

Yes. I know that this is the way VNC works in general. 
I was not wondering about that.

Thanks, though. I appreciate the help here. 
What a great community.

---

