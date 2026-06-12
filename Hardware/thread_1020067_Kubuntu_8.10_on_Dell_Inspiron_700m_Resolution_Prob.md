---
title: "Kubuntu 8.10 on Dell Inspiron 700m Resolution Problems"
date: 2008-12-23
forum: Hardware
---

### Post by tomahawk77 on 2008-12-23
I just installed Kubuntu on Dell 700m and the resolution looks pretty poor. Though it shows up as "1280X800" but it is far from it. While it is booting up, it seems to be the right resolution (with all pretty icons and all) but once it boots up, everything goes haywire ... Any known issues here? 

I would appreciate any help. I am not a proficient linux user ...

Thank you all in advance.

---

### Post by tommcd on 2008-12-24
> **tomahawk77 said:**
>  Though it shows up as "1280X800" but it is far from it. 


If you think the indicated resolution is not accurate, go to this website to see what resolution you are actually using:
[http://whatismyscreenresolution.com/](http://whatismyscreenresolution.com/) 
If that site says it is 1280x800, then it probably is.
And see this about fixing screen resolution problems in Ubuntu:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

For safety, before making any changes to your resolution, back up your xorg.conf first like this:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

---

### Post by tomahawk77 on 2008-12-31
Thanks for the reply, and my apologies for the delay. 

So I did as you had suggested and changed the resolution to 1280X800. I think the issue is that my laptop screen is very small (about 12inches I think) and everything on the screen shows up as if it were being displayed on a 21inch monitor. I was referring to the "scaling" as opposed to resolution. For example the "Start" menu shows up humongous icons and fonts. It's pretty much the same with any other window I open. Any suggestions? 

Thanks again.

---

