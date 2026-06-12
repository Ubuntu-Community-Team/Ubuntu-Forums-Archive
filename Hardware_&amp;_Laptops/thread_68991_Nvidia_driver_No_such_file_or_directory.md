---
title: "Nvidia driver: No such file or directory???"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by SquinkyEye on 2005-09-24
Can someone please help,

I'm stuck on user tseliot "How to: Latest Nvidia drivers" post.

On # 2 it states: "remove the file manually" "sudo rm /etc/init.d/nvidia-glx" I type this sudo command and press enter, it asks for my password, I enter this and press enter again. This is the error message I receive. "rm: cannot remove `/etc/init.d/nvidia-glx': no such file or directory"

When I search in synaptic for "nvidia-glx" it's there but not installed/highlighted so am I supposed to get a "no such file or directory" message or not?

However, I get the same "no such file or directory" error message a few lines further down tseliots post where I'm supposed to extract the driver. In my case its the latest 7676 driver so when I type "sudo sh NVIDIA-Linix-x86-1.0-7676-pkg1.run" I get the error message.

I have the latest kernel for my 2.6.10-5-386 and installed gcc as instructed so what could be wrong?

Any help would be very appreciated.

BTW...I'm using hoary with all updates installed. Video card is a MSI Ti4800se - MB is a Intel D845bg - P4 2.4Ghz - 512Mb ddr ram, and I'm brand spanking new to Linux yet still willing to learn :)

---

### Post by Gezzer on 2005-09-25
To enable the driver, run 

sudo nvidia-glx-config enable

---

### Post by SquinkyEye on 2005-09-25
Thanks for your response Geezer. I'm not sure if the enable command you recommend would work or not (perhaps I'll try it later). But I'm not sure if I'll need to. 

After my original post I found the link "How to install graphic driver (NVIDIA)?" posted at the Unofficial guide. I tried the guide and finally got a Nvidia driver working on Ubuntu (my first working Nvidia driver). Guess I should have looked for this post first. :)

But I should have clarified why I wanted the latest Nvidia driver in my original post. Movies, whether streaming Mpeg's, avi's, or avi's stored on my hard drive, all have no color, are choppy, and have poor audio video sync.

Since I have (I think) all the latest codecs installed I assumed it was the video driver. It's probably not the video driver but perhaps the codecs aren't the latest? Or perhaps it's the Totem player? I tried Totem-xine but the video problems remain.

At least I did solve one problem, the screensavers are smoking fast now that I've got the basic Nvidia driver installed...he he :)

So, if you or anyone else has a clue how to solve my movie playing problems I'd be most grateful. Maybe a link or tutorial on how to REALLY get all codecs setup is all I need since I got all the gstreamer updates (again, I think). Thanks in advance.

---

