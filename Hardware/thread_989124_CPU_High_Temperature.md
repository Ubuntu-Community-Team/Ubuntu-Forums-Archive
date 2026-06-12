---
title: "CPU High Temperature"
date: 2008-11-21
forum: Hardware
---

### Post by zeroed on 2008-11-21
Guys, 
Are you going to fix problem with high cpu temperature?

---

### Post by sirjoebob on 2008-11-21
Nope. What is "high" and what are your system specs, manufacturer, etc???

---

### Post by zeroed on 2008-11-21
> **sirjoebob said:**
> Nope. What is "high" and what are your system specs, manufacturer, etc???

Dell Inspiron 1501.
After installing 8.10 - I can not use it at all.
Fans just don't work and computer became very hot, even if I will do nothing.
After that, of course, computer halts.

It's not only my problem, you can find similar bugs in lanchpad.

Here is my bug:

[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/300494](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/300494)

For you to understand the problem:

I will not use 8.10, just because I can not. If some newcomer will have the same problems - he will not use Ubuntu at all. The reason is simple: he wants his computer to be safe.

If you don't care about it - ....

---

### Post by sirjoebob on 2008-11-21
> Dell Inspiron 1501.

That's what I expected to hear...

Dell laptops have issues with fan support. Best way to rectify is by installing gkrellm and i8k-utils. There are good tutorials for doing this and can be found pretty easily on Google. I will try to find some and post to this thread.

---

### Post by zeroed on 2008-11-21
> **sirjoebob said:**
> That's what I expected to hear...

Dell laptops have issues with fan support. Best way to rectify is by installing gkrellm and i8k-utils. There are good tutorials for doing this and can be found pretty easily on Google. I will try to find some and post to this thread.

Hm... very strange O_o

Why everything is ok on 8.04?

I don't have i8k-utils installed on it at all.

---

### Post by sirjoebob on 2008-11-21
No idea. But check [this lin]("http://sirjoebob.livejournal.com/3297.html")k for installing and configuring gkrellm to monitor and controll the fans.

---

### Post by zeroed on 2008-11-21
> **sirjoebob said:**
> No idea. But check [this lin]("http://sirjoebob.livejournal.com/3297.html")k for installing and configuring gkrellm to monitor and controll the fans.


didn't help. I couldn't apply plugin: gkrellm failed to install it.

---

### Post by zeroed on 2008-11-21
I just don't understand, what is the problem?

Just some package?

Everything is very good on 8.04.

---

### Post by sirjoebob on 2008-11-21
I have always had to use gkrellm for my fans on my dell... and everyone I know has had the same issue.
> 
I couldn't apply plugin: gkrellm failed to install it.

What do you mean by this? Did you get an error? Are you running Ubuntu 64 bit or 32 bit? Also, did you try installing from synaptic or terminal?

---

### Post by zeroed on 2008-11-21
> **sirjoebob said:**
> I have always had to use gkrellm for my fans on my dell... and everyone I know has had the same issue.


What do you mean by this? Did you get an error? Are you running Ubuntu 64 bit or 32 bit? Also, did you try installing from synaptic or terminal?

I have never had such problems untill 8.10. 

Yes, I get an error. I'm running ubuntu 32 bit. I have installed everything in terminal.

---

### Post by zeroed on 2008-11-21
ubuntu1501.com

try to find this problem here: I couldn't. Nobody on 1501 had such a problem.. I think...

---

### Post by sirjoebob on 2008-11-21
Post your error so I can take a look.

---

### Post by zeroed on 2008-11-21
> **sirjoebob said:**
> Post your error so I can take a look.

please, have a look at attachments.

also notice, that applet shows wrong data.

---

### Post by sirjoebob on 2008-11-21
The sensor applet (to my knowledge) cant detect proper settings from dell laptop fans. Also, I do not have any clue about your error. Maybe try and install through synaptic... Very strange. It may be over my head to help you with this one.

---

### Post by zeroed on 2008-11-21
> **sirjoebob said:**
> The sensor applet (to my knowledge) cant detect proper settings from dell laptop fans. Also, I do not have any clue about your error. Maybe try and install through synaptic... Very strange. It may be over my head to help you with this one.

Is there any difference using sudo apt-get or synaptic?

---

### Post by sirjoebob on 2008-11-21
Not really, but synaptic is graphical, there is less room for user error and may at least give you more feedback.

---

### Post by zeroed on 2008-11-21
> **sirjoebob said:**
> Not really, but synaptic is graphical, there is less room for user error and may at least give you more feedback.

There were no errors, everything was installed successfully..

---

### Post by sirjoebob on 2008-11-21
I mean try to reomove and reinstall the gkrellm-i8k package through synaptic. did you follow all the other steps in the link i gave you earlier?

---

### Post by dereferenced on 2008-11-21
No everything is not ok on 8.04 too.. my laptop (hp presario 5000v) acts weird and goes to near 100 degrees centigrade (that is what it says when it automatically gets switched off) even when I am just watching a movie or downloading from ubuntu regular updates.. 

life has become nightmare.. fans just keep rotating and wont just stop and make a lot of noise.. I dont know if its my systemm problem or the operating system's.

please advice.

---

### Post by zeroed on 2008-11-21
[http://ubuntuforums.org/showthread.php?t=965029]("http://ubuntuforums.org/showthread.php?t=965029")

We are not alone.

I'm still sure it's a problem of 8.10

I have the latest BIOS.

---

### Post by zeroed on 2008-11-21
> **dereferenced said:**
> No everything is not ok on 8.04 too.. my laptop (hp presario 5000v) acts weird and goes to near 100 degrees centigrade (that is what it says when it automatically gets switched off) even when I am just watching a movie or downloading from ubuntu regular updates.. 

life has become nightmare.. fans just keep rotating and wont just stop and make a lot of noise.. I dont know if its my systemm problem or the operating system's.

please advice.

I agree with you completly!

---

### Post by zeroed on 2008-11-21
```
z@z-laptop:~$ acpi -V
     Battery 0: Charging, 48%, 00:00:45 until charged
  AC Adapter 0: on-line
     Thermal 0: ok, 80.0 degrees C
     Cooling 0: LCD 0 of 7
     Cooling 1: Processor 0 of 0
     Cooling 2: Processor 0 of 7
```

---

### Post by Gausian on 2008-11-21
are xps laptops not affected by this problem?  cause my temps are fine.

---

### Post by zeroed on 2008-11-21
Have found the same problem like my one:

[https://bugs.launchpad.net/ubuntu/+bug/292713]("https://bugs.launchpad.net/ubuntu/+bug/292713")

And again 8.10

---

### Post by cariboo on 2008-11-21
My suggestion would be to reinstall Hardy until the bug is fixed, unless there is a compelling reason to use intrepid.

Jim

---

### Post by zeroed on 2008-11-21
> **cariboo907 said:**
> My suggestion would be to reinstall Hardy until the bug is fixed, unless there is a compelling reason to use intrepid.

Jim

Yes, I'm going to do it.

The reason to have interpid installed - I have a website about ubunu. But know I will stop to support it..

Are you sure that the bug will ever be solved?

I have found a couple of the same bugs even in 6.04 that were closed as unresolved.

---

### Post by ciscosurfer on 2008-11-21
> **zeroed said:**
> Yes, I'm going to do it.

The reason to have interpid installed - I have a website about ubunu. But know I will stop to support it..

Are you sure that the bug will ever be solved?

I have found a couple of the same bugs even in 6.04 that were closed as unresolved.I agree with cariboo907. 

Can you clarify what you mean?  What does using Intrepid (8.10) have anything to do with a website about Ubuntu?  If you've had better luck using Hardy (8.04) then you should reinstall that version of the OS.

---

### Post by zeroed on 2008-11-21
> **ciscosurfer said:**
> I agree with cariboo907. 

Can you clarify what you mean?  What does using Intrepid (8.10) have anything to do with a website about Ubuntu?  If you've had better luck using Hardy (8.04) then you should reinstall that version of the OS.

The specific of my web site: it is how-to for newcomers. It's important to understand. Usually newcomers have a lot of problems with simple things. For example, when you install 8.04 and choose russian (my web site is russian) - default keyboard is not what user usually want. So, there are a lot of questions on web forum like "I try to type question symbol, but can not do it, bla bla bla". The solution is to choose "Winkeys". This is just a simple example. The user wants to see the good correct answer. They call it "userfriendly help".

I use a lot of pictures and describe all carefully. 8.10 has changed, so I have to update my website. I'm not sure that newcomer will choose 8.04, just because it's LTS. He will not care about it, anybody loves new features. And me too.

And, for example: [http://zeroed.ru/ubuntu/installation#partitions-setup](http://zeroed.ru/ubuntu/installation#partitions-setup)

You can see pictures from 8.10, not from 8.04. I know, it's a little change, but the user think other way.

Believe me, I know it.

Another example: [http://zeroed.ru/ubuntu/gnome](http://zeroed.ru/ubuntu/gnome)

8.10 use another way to restart (logoff, shutdown..) the system then 8.04

---

### Post by zeroed on 2008-12-02
The problem was solved.

It was in bios settings.

"Power now" was turned off.

Why have I turned it off? VMWare machines asked me long time ago.. =)

---

### Post by alibabahck on 2009-01-24
I'm running a Dell 1501 which did have a problem with high CPU temperatures. The Dell 1501 fan is controlled through the BIOS and not by the operating system. I pulled apart my machine and cleared out the cooling fins with compressed air and after that I didn't have a problem. It's possible that your running your computer a bit harder since using 8.10 or the dust build up has reached a critical level.

---

