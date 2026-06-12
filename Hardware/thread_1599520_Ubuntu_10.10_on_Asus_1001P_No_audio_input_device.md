---
title: "Ubuntu 10.10 on Asus 1001P No audio input device"
date: 2010-10-17
forum: Hardware
---

### Post by kardizen on 2010-10-17
I've recently installed Ubuntu 10.10 Netbook Remix for my Asus 1001P.  Everything seems to work fine but I couldn't get the microphone to work.  I've looked for solutions and found some for 10.04 such as getting Karmic-generic but the sudo command does not work.  I tried to download the file somewhere and the source center would not install it.  I have the pulse audio app but on the input tab there is nothing.  In the sound options no device shows up on the input tab either.  Any advice on how to get the microphone to work?

---

### Post by tru infini on 2010-11-15
I'm having the same problem. Is it something wrong with the whole of 10.10? when i installed zynadd it directed my sound output to a file that didn't exist with no seemingly curable solution. I am this close --> <-- to downgrtading to 10.04 or even 9.10 to get the programs I like to work again,...

---

### Post by ophysis on 2010-12-06
+1 
Anyone?

---

### Post by kardizen on 2010-12-06
> **ophysis said:**
> +1 
Anyone?

I fixed my issue awhile back.  I was something really stupid.  In my sound preference under Hardware, I had 'Analog Stereo Output' selected as the profile.  Once I changed it to 'Analog Stereo Duplex', everything worked fine.

---

### Post by tru infini on 2010-12-06
I wish changing mine to Analog Stero Duplex would have fixed mine. I've downgraded to 10.04 and have fixed my zynadd problems,...now if i can get my stupid mic inputs on the front and back to work i'll be happy. i don't seem to have very much microphone options on here.

---

### Post by cdeem on 2010-12-21
> I fixed my issue awhile back.  I was something really stupid.  In my  sound preference under Hardware, I had 'Analog Stereo Output' selected  as the profile.  Once I changed it to 'Analog Stereo Duplex', everything  worked fine.     Thank you. I would have given up long before I found that :D

I'm still using 10.10. For the options I installed gnome-alsamixer and just played with all the sliders till I got a halfway decent result.

---

