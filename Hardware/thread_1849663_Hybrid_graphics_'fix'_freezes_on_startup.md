---
title: "Hybrid graphics 'fix' freezes on startup"
date: 2011-09-24
forum: Hardware
---

### Post by ..sam.. on 2011-09-24
Hi,
I am trying to turn my hybrid graphics cards on and off, but I am running into a few problems. 

When I run  'cat /sys/kernel/debug/vgaswitcheroo/switch':
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Pwr:0000:01:00.0
```
So I am not sure if I can make this work. I don't seem to be able to switch them or turn either on or off.

When I follow the instructions on: [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
My computer freezes on startup, running 'echo OFF > /sys/kernel/debug/vgaswitcheroo/switch' causes this when run in the terminal but it shouldn't do it on startup. 

Any suggestions?

---

### Post by Clicksights on 2011-09-27
there is another threat:
[http://ubuntuforums.org/showthread.php?t=1849642](http://ubuntuforums.org/showthread.php?t=1849642)

Where i gave this advice:

Meet the transformers :wink:


I have also an Optimus set-up on my MSI X460DX
I took me a bit but i now am from 60Fps up to 600Fps if i use bumblebee. :razz:
Bumblebee works great if you want to use the power of your extra graphics card.

You can switch your extra card off with the help of ironhide.
That will increase the battery bij a few hours! :razz:
I didn't try Ironhide yet.

the inventor:
[http://www.martin-juhl.dk/2011/08/ir...ting-for-duty/]("http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/")
ironhide
[https://launchpad.net/~mj-casalogic/+archive/ironhide/]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/")
bumblebee:
[https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee)

Some laptops have a bios option to switch the extra card off.
Hope this helps.

(You need both drivers installed, for both the onboard card and the extra card!)

my 2 beans...

---

### Post by ..sam.. on 2011-10-01
>  (You need both drivers installed, for both the onboard card and the extra card!)
Is this for the switcharoo commands and everything to work?

Thanks for all the useful links. When I upgrade to 11.10 I will give all those a try.

---

### Post by Clicksights on 2011-10-05
I use bumblebee, and it works perfect.
The switching on/off of the second gpu is also possible with the newest release.
I didn't try it yet, having some other trouble with my laptop (can't find /home anymore while booting!) 

I got the switching working with Ironhide though.
But the drivers didn't load. Don't know what i did wrong. 
I want to try the switching with Bumblebee asap.
It will ad over 2 hours to my battery life! (Up to 4 if i was to believe MSI...:P )

give it a try, there is a short description on the website/in the read me of Bumblebee,
for Ironhide i couldn't find one. :-(

---

