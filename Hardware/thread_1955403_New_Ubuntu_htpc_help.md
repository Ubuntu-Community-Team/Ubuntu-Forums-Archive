---
title: "New Ubuntu htpc help"
date: 2012-04-09
forum: Hardware
---

### Post by Tomcat7810 on 2012-04-09
Hello,
 I am about to pull the trigger on a Ubuntu htpc build using a amd apu a6 3500 and 4gb ddr3 1600 ram. I want to just install it on a 32gb ssd and stream the videos from my main pc a windows 7 i5 2500k. My question is what is the best way to stream the videos to xbmc in Ubuntu, can I just map a drive or will I have to use something like samba? Also is there any recommendations you have on my processor choice? It is a pretty low budget build so thats why I was looking at the apu. But any recommendations would be greatly appreciated.
Thanks!

---

### Post by Tomcat7810 on 2012-04-10
Anyone have any recommendations. I mainly am just wondering how well the apu graphics work with Ubuntu, as well as any recommended programs I should install to better my home theater pc besides xbmc.

---

### Post by kiirokurisu on 2012-04-10
Your question would probably be better-answered in the XBMC forums.

---

### Post by papibe on 2012-04-10
Hi Tomcat7810.

Do not stream. Share instead ;) Either Samba or NFS will work great.

Streaming is better left when the receiving device has hardware/codec limitations (like a game console or an IP speaker).

Regards.

---

### Post by Tomcat7810 on 2012-04-11
Ok cool, so would a 30gb ssd do fine to hold Ubuntu with xbmc. I know when it comes to windows 30gb is really pushing it but I think that the overall install of Ubuntu is very little in space correct?

---

### Post by kiirokurisu on 2012-04-11
30GB is plenty for a full Ubuntu install plus extras. I usually allow 15GB and have never exhausted even that much.

---

### Post by papibe on 2012-04-11
> **kiirokurisu said:**
> 30GB is plenty for a full Ubuntu install...
+1

I would recommend not separating root (/) from /home so you take advantage of the whole space. Also, since you'll be using a SSD and have plenty of RAM, I wouldn't use any swap space.

Regarding the AMD APU CPU, your main concern is the support for video hardware acceleration. You need to research about VAAPI support on AMD CPUs. As mention before the XBMC forums are the best place for that. For example take a look at this thread: [HOW-TO use VAAPI HW Acceleration on AMD Zacate (Fusion) platform]("http://forum.xbmc.org/showthread.php?tid=99154&highlight=APU+VAAPI").

Regards.

---

### Post by Tomcat7810 on 2012-04-11
Ok yea I will check that out. So you think that processor will not studded or skip on blueray movies. The 2.1ghz concerned me a little bit?

---

