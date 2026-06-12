---
title: "HP Pavillion dv9925nr builtin mic issue"
date: 2008-09-02
forum: Hardware
---

### Post by Nawaf on 2008-09-02
Hello

I need help with getting my friend's HP Pavillion dv9925nr, AMD Turion X2 64-bit processor, to be able "to hear me". Ubuntu doesn't seem to recognize the built-in microphone although the built-in webcam works just fine.

Any help is deeply appreciated

---

### Post by anglina on 2009-07-16
I have been PLAGUED with the problem of getting all of my onboard hardware on my HP DV9925NR to work. 

I kept a small windows install on the side just to do simple wireless or Skype use as needed. I looked for WEEKS for a solution. Scoured the forums. There WAS nothing.

Onboard Mic didn't work, Wireless card didn't work properly

Those are kinda big issues for me. 

I run a small computer repair business and I would have to boot into my windows install just to check someone's wireless router for them. (No way I am carrying cable, I know I'm a snob)

I was able to get everything to work perfectly by upgrading to Karmic. To upgrade to Karmic, use update-manager -d
[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)
It mentioned using the run command hotkey (Alt-F2) but I just did it in terminal. [Yakuake actually ;)] [http://en.wikipedia.org/wiki/Yakuake](http://en.wikipedia.org/wiki/Yakuake)


Remember Karmic is in Alpha and if you are not a fan of Alpha then your loss. I have NEVER had problems with Karmic. Everything works. You couldn't get me to believe that it is an Alpha and not a full release!!

Downloaded and Installed the updates followed by restarts then installed Skype like I usually do by adding the Medibuntu Repository followed by sudo apt-get install skype
[http://www.clububuntu.com/2009/04/how-to-add-medibuntu-repository.html](http://www.clububuntu.com/2009/04/how-to-add-medibuntu-repository.html)

Did my test call and it finally worked.

To get my NVIDIA Graphics and Wireless to Work I had to enable the use of the drivers.

System -> Administration -> Hardware Drivers

Click the balls to the left of the drivers to turn them green (meaning on) and restart. The Wireless drivers make the wireless card work great and you can use the switch too! I had found a way on a different post about using a command line thing to get it to work but you had to do a bunch of stuff to get it to work and you had to do it every time. UGH!

Hope this helps anybody!!

---

