---
title: "DELL M1330 Ubuntu-9.04, Playback sound Pops and Squeaks when I watch Video.."
date: 2009-06-15
forum: Hardware
---

### Post by VipX1 on 2009-06-15
[B]Hi Guys,[-X
[/B]I watch lots of tutorial videos on my Laptop**,** both with** movie player** and on **youtube** and some lecters on the college web site. I've been using [COLOR=Sienna]**Ubuntu**[/COLOR] for 2 xmonths now about. I work with the **OS** that should not be mentioned five days a week so I want my own **PC** to be different, completely and**[COLOR=Sienna] Ubuntu[/COLOR]** fits the bill very nicely. I've only  1 x problem and thats with the sound..
When I watch a video on youtube the sound goes completely after 2 minutes of the video playing. While it is working for thise 2 minutes it pops, squeaks, scratches and makesreally digital sounding noises. It's likethe inner workings of my lap-top are being amplified along with the sound from the video. If I download the samw video and play it on movie player it will play all the way threw from start to finish with sound working but I still have all the digital noises. If anything it is worse! There are some graphical misdemeanors too but I'll not go into them here unless I'm asked. 
My techincal statistics are published [[SIZE=3]**here**[/SIZE]]("http://www.alsa-project.org/db/?f=69e6827c04529394125bc3d34ba4bedce8baba2f"). They were only uploaded today.
I had the Alsa-1.0.18rc3 driver installed originally. Using the 'sound problems' page I've got the driver updated to Alsa-1.0.20 but it gave me the very same pops and squeaks..:(
I love using [COLOR=Sienna]**Ubuntu**[/COLOR], big time, so any and all help will be much appreciated.

---

### Post by VipX1 on 2009-06-17
[SIZE=3]I would like to add some info about the audio problem and also bring this problem to your attention again.[/SIZE]
[SIZE=3]The volume control on the Youtube video display GUI doesn't effect the playback audio level. Also, the hardware volume control on the laptop turns the Capture volume up and down and not the Master. Is this just because they're patched threw incorrectly and if so how do I reconfigure them correctly.:?:
If anybody has audio problems with a  M1330 with 9.04 jaunty let me know...](*,)
[/SIZE]

---

### Post by VipX1 on 2009-06-18
[SIZE=3]Hmm[/SIZE], could [this]("http://www.pulseaudio.org/ticket/322") be the problem I'm having with the sound on my M1330?

---

### Post by VipX1 on 2009-06-27
I would just like to post my solution  to this for people who end up on this page when looking for a solution...
In synaptic I reinstalled the primary Pulse file pulseaudio and then followed part A of [THIS]("http://ubuntuforums.org/showthread.php?t=789578") page. I didn't have all the folders to back up or erase only the first one that is mentioned in the command line. Maybe was the problem? I had them after I'd done these few things...  Then I rebooted.
God helps those who help themselves!

---

### Post by VipX1 on 2009-07-22
[solved]
I had swfdec-mozilla installed and and I had the correct flash players in Firefox installed. Two different flash players were playing the Youtube Video at the same time. It was better when I re-installed the Pulse s/w but it was perfect when I removed swfdec. If you type *about:plugins* into the Firefox address bar at the top of the web browser you should only have  Shockwave Flash and FutureSplash Player listed and enabled. The problem wasn't the audio set-up.

---

