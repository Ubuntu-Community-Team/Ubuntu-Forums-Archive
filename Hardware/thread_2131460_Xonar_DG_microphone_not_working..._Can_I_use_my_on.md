---
title: "Xonar DG microphone not working... Can I use my onboard sound mic?"
date: 2013-04-01
forum: Hardware
---

### Post by Dobly on 2013-04-01
I have a Xonar DG sound card working great in Ubuntu 12.10. It has a built in headphone amp and it sounds amazing. 

However the microphone does not work. 

I have poked around online and it seems many users have this issue. Even the Alsa page lists this card as 'working', but 'microphone not working'. 

My Gigabyte motherboard has onboard sound and a mic input. The exact brand of this is not relevent to me question. 

My plan is to use the Xonar DG for sound, but use the Mic input on the motherboard. 

Here are my questions. 

1. Is this feasible, assuming my on board sound chip is supported. I mean am I wasting my time trying to have two sound chips active?
2. Were would I start with this project? What would be my steps to getting this happening. What am I going to need? I am a noob when it comes to configuring hardware. 
3. When I go to bios and reactivate my onboard sound, will Ubuntu potentially  
      a. do nothing 
      b. crash 
      c. maybe just maybe ,see the new hardware and automatically install drivers for it? 

What am I in for with this project?

Cheers

---

### Post by Dobly on 2013-04-02
Well, for those who may read this and ponder the same issue, let me tell you it was the easiest thing to do. 

First up, my on board sound chip a Realtek ALC889. 

I set it to active in bios and started Ubuntu 12.10. 

Once in I ran 'alsamixer' from the terminal. In there I could press F6 and select the on board 889 chip. Alas had found it already. Furthermore, I was able to go to it's mic input and turn it up from 0. 

So far so good. 

Then in Ubuntu I ran the Sound control panel. In the input tab I was able to select the on board mic input. And what do you know, it worked!

This all went so well I learned nothing about how this stuff works. It just worked, and worked very very well. Hats off to the dudes who coded this stuff.

So now I have my sound coming out of the Xonar DG and all it's 'headphone amp' goodness, and  I have the mic input going into the motherboards mic input. Awesome.

---

### Post by ubuntownick on 2013-06-18
Works for me once, but now mic is present for Audacity and all other stuff but not for skype. Enyone knows what to do?

---

