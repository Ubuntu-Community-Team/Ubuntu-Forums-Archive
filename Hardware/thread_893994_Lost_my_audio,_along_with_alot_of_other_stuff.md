---
title: "Lost my audio, along with alot of other stuff"
date: 2008-08-18
forum: Hardware
---

### Post by bluekeys on 2008-08-18
I had Ubuntu working perfectly fine with everything pimped out to how I wanted it.

Then I found something to remove orphaned packages. I started using it and removed all orphaned packages. Now I'm missing TONS of stuff that I used to have/use, and my sound no longer works.

Volume Control shows that it is muted, and when I try to change it, I get this error:
[IMG]http://img46.imageshack.us/img46/3699/screenshotgnomevolumecotg6.png[/IMG]

I have looked all over the internet for information on how to fix this, but I simply have found no answers.

What should I do to fix this?


Edit:
I looked at a device manager and here is the information it is giving about Audio:
Model: MCP67 High Definition Audio
Vendor: nVidia Corporation (Hewlett-Packard Company)
Connection: PCI (Peripheral Component Interconnect)

I have lost QUITE a bit of other stuff too, such as gdebi. How can I retrieve everything that comes stock?

---

### Post by pwnprog on 2008-08-18
any way to find out which packages it deleted? my only idea is to get the full list and re-install them in synaptic package manager

---

### Post by pwnprog on 2008-08-18
and btw... im glad i read this thread. i have one of those orphaned package thingys and am now REMOVING it!

---

### Post by bluekeys on 2008-08-18
I don't think there is any way to see what all it removed. It deleted A LOT of stuff though, I know that.
Luckily, my nvidia graphics drivers and networks drivers are still intact.
I just don't know what I'm missing as far as sound goes. I don't know how to check what it removed, but for some reason now it isn't finding my device.

I have tried re-installing alsa and gstreamer but have had no luck in getting anything different.

---

### Post by pwnprog on 2008-08-18
try this. go into synaptic package manager (system->administration->synaptic package manager)

then you can go into file-> history


this should (in theory) tell you every package that you ever added, removed, updated, or farted on. how would you fart on a package?? .... not so sure

so ya... unless somebody comes in and tells you otherwise, i'd say your best bet is to make a little list of the name of each package you think the orphaned package screwer-upper deleted, and go re-install it. 

you can also do that in synaptic by finding the packages on that big list, and clicking the boxes beside them. you will want to choose "mark for installation" in this case. once you think you got em all, apply the changes, wait, listen to some RUSH, and hopefully by the end of "tom sawyer" you should have a working linux computer again.

---

### Post by bluekeys on 2008-08-18
I tried looking at the history in synaptic. It doesn't list what was removed by the orphaned package remover, only the things I removed through synaptic or Add/Remove Programs.

So I'm still stuck, but still searching. Any other suggestions?

Your help is greatly appreciated.

---

### Post by Dreamerman on 2008-08-19
> **bluekeys said:**
> I tried looking at the history in synaptic. It doesn't list what was removed by the orphaned package remover, only the things I removed through synaptic or Add/Remove Programs.

So I'm still stuck, but still searching. Any other suggestions?

Your help is greatly appreciated.

Hey, you won't like this but better to reinstall Ubuntu again. Happened to me & found out that reinstalling is better use of time than finding out what/how went wrong.

I installed Xubuntu recently & removed excess apps. Everything went wrong after that. Spent the next hour reinstalling everything.

Good luck.

---

### Post by bluekeys on 2008-08-19
I can't have that. There is absolutely NO way of getting back to where I was without starting over?

---

### Post by bluekeys on 2008-08-19
I logged into an IRC chat and after a long while of chatting, someone suggested I check out dpkg.log

So I ran this command: matt@matt-laptop:~$ gedit /var/log/dpkg.log

And here is just a tiny tiny section of the file:
[http://paste.ubuntu.com/38720/](http://paste.ubuntu.com/38720/)

I used Firefox's CTRL + F to find every remove entry and went through synaptic searching each thing that was removed, and marking them for installation.

A lot of gstreamer packages got removed, along with quite a few ALSA packages.

Another two very important packages that were removed were these two:
```
ubuntu-minimal
ubuntu-standard
```

I am still installing stuff and it doesn't work yet, but it's an update.

---

### Post by bluekeys on 2008-08-19
That didn't help at all.

This sucks.

---

