---
title: "realtek driver install help (n00b)"
date: 2009-05-01
forum: Hardware
---

### Post by jc1993 on 2009-05-01
right ive got linux on my computer, everything worked out correctly, even the nvidia driver installed correctly.
however, the realtek driver appears not to work, as i get no sound whatsoever, not even at startup.
can anyone help me? the driver ive got:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")

my system is a lenovo 3000 n200 0768 BRG

thanks in advance

---

### Post by mirnander on 2009-05-21
I am completely new to ubuntu and I've had some problems with my realtek driver and invidia sound card as well. At first after install, the sound was fine. Then I installed an update, at ubuntu's suggestion, and my sound disappeared. :(  

I found a little help by googling and found that I had to open the terminal and type "alsamixer" 

That brought up some hidden things to tweak and play around with. Sorry I don't have a screen shot.

Try googling "alsamixer" and see if you can find that thread for yourself.  I messed around with the controls and got the sound going again, but now I've got horrible buffering issues going on. 

My sound pops and clicks as if the cpu is overloaded, but my cpu is never over %50 when this happens. I'm also getting problems with getting the proper playback speed when first playing an audio file.

In case anyone else comes across this and has 2 cents to add, here's what I've got: 

Card: HDA NVidia                                                             &#9474;
Chip: Realtek ALC880    

I'm getting sound working under the "advanced linux sound architecture" and the "HDA analogue Nvidia ALC880 Analogue," setting in the sound dialogue under system preferences, but still.... buffering issues abound. (At least I think this is a buffering issue. I am a noob after all.)

I read something about this possible being an issue with a kernel update, but I've got nothing to roll back to on boot up, so dunno...

P.S - I think the ubuntu community is more likely to respond if you give as much detail as possible with your problem. ie: my sound card is a... on windows I use driver...

---

