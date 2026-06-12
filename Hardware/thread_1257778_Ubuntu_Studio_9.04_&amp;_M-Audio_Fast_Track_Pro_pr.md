---
title: "Ubuntu Studio 9.04 &amp; M-Audio Fast Track Pro problems"
date: 2009-09-04
forum: Hardware
---

### Post by g-raf on 2009-09-04
I recently got an M-Audio Fast Track Pro sound card and I'm trying to use it to record audio through Jack in Audacity, but I can't run Jack in realtime using the Fast Track Pro and get Audacity to recognize the sound card through Jack. Here are screenshots of the problems I'm dealing with.
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/040729167.jpg[/IMG]
In my Sound Preferences, the Fast Track Pro is not recognized under "devices," only the ALSA mixer and OSS mixer are recognized.
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/040730435.jpg[/IMG]
In the "sound capture" preferences, M-Audio FastTrack Pro USB Audio #1 (ALSA) is recognized, but not the regular M-Audio FastTrack Pro USB Audio (ALSA). I don't know what the #1 means, or if it is a problem or not.
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/040733273.jpg[/IMG]
This is how I have the Jack server set up. The interface "hw:1" is "FastTrack Pro" and the input device "hw:1,1" is "USB Audio #1".
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/040736042.jpg[/IMG]
This is what happens when I try to start the Jack server.
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/040737101.jpg[/IMG]
When I open Jack in the terminal ($ sudo qjackctl), then I can run Jack in realtime since i have the permissions by opening it in the terminal. However, in the screenshots below, you will see that Jack is not recognized as a playback or a recording device in Audacity when i try to set it up for use.
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/040739564.jpg[/IMG]
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/040740244.jpg[/IMG]
When I stop the Jack server, then I can select the ALSA FastTrack to record.
However, when I do record, it will only record on the left channel (not both channels) in Audacity. Also, the sound quality is horrible. Sound scratchy and crappy.
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/040744067.jpg[/IMG]

I'm trying to set up my own home recording studio with Ubuntu Studio and various hardware (when i get it). I'm trying to take the first step by using a high quality external sound card (audio interface) for recording and producing. However, I can't get it set up and it's driving me nuts. I'm not much of an expert when it comes to coding and use of software in Ubuntu. But I'm determined to do it. 
  
 If anyone can offer some advice on how to get the M-Audio Fast Track Pro to work in Ubuntu Studio using Jack and Audacity for recording, that would help me so much. Thanks.

---

### Post by g-raf on 2009-09-05
There are also two new problems that I've encountered after a day of tinkering:

1) Jack is working in realtime now, however, Jack is not recognized as an input or an output in Audacity preferences. I can't record audio using Jack and the Fast Track Pro soundcard.

2) My realtime kernel freezes at the login screen.

Do i need to use the realtime kernel for best results? How can i get Audacity to recognize the Jack server?

---

### Post by g-raf on 2009-09-06
Please help me out. I use Jack & Audacity for professional purposes and need to fix it right away. 

The problem is that Audacity doesn't recognize Jack as an input or output device when i run Jack in realtime using the M-Audio Fast Track Pro soundcard as an interface and input device.

If more information can help, I can give any information. Just let me know what kind of information is needed. Thanks.

---

### Post by g-raf on 2009-09-07
Still having the same problems, have found no solutions. Audacity, Audacious and Hydrogen all don't recognize Jack when it's running. Can't connect to Jack. At this point, i don't think the problem has to do with the soundcard. Jack isn't working with other programs and it's shut me down for days. I have nothing to do but consider returning to windows. Any suggestions, thoughts or ideas would be really helpful.

---

### Post by KrazyFox on 2009-09-11
Hi G-raf,

i am starting up with audio production on linux.

I installed ubuntustudio a few days ago. 
My hardware is the m-audios fast track pro.

I can testify that it works.

I get audio via jack from audacity, hydrogen and creox simultaneous.

But i am not satisfied yet, the latency is to high.

Did you make progress? If not, I hope I can help you.

---

### Post by KrazyFox on 2009-09-11
Another issue, after a while (?) (e.g. writing the above post) the sound output get faulty. Sounds like a transformer scratch, about 3 interrupts per second.

What I did is: 

  - stopped the sound
  - opened firefox and did some browsing
  - started the sound again --> output is faulty.


jack doesnt show xruns.

I am sure , if I reboot my machine. the sound is proper again.

Hm, anybody?

---

