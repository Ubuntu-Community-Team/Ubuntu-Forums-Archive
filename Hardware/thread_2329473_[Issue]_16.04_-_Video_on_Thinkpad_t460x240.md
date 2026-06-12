---
title: "[Issue] 16.04 - Video on Thinkpad t460/x240"
date: 2016-07-02
forum: Hardware
---

### Post by Krophil' on 2016-07-02
Hello,
I am experiencing a strange issue when watching video with any video application. Indeed, when I launch a video, I see the default format of it (generally smaller than the screen) and a blue background around. Moreover, the video itself stays foreground when I switch to another window.

I have 4.4.8-040408 kernel (with Xubuntu 16.04-04). I had the same problem with 4.4.0 kernel and/or Xubuntu 14.04-04.

[FONT=&amp]Processeur Intel Core i5-6200U
[FONT=&amp]Intel HD Graphics 520[/FONT]
[/FONT]
I think it is a common problem to t460, x240 and others because a friend of mine has the same problem.

Do you have any idea of the source of the problem ?

Thanks for your help.

---

### Post by sk1d on 2016-07-28
> **Krophil' said:**
> Hello,
I am experiencing a strange issue when watching video with any video application. Indeed, when I launch a video, I see the default format of it (generally smaller than the screen) and a blue background around. Moreover, the video itself stays foreground when I switch to another window.

I have 4.4.8-040408 kernel (with Xubuntu 16.04-04). I had the same problem with 4.4.0 kernel and/or Xubuntu 14.04-04.

[FONT=&amp]Processeur Intel Core i5-6200U
[FONT=&amp]Intel HD Graphics 520[/FONT]
[/FONT]
I think it is a common problem to t460, x240 and others because a friend of mine has the same problem.

Do you have any idea of the source of the problem ?

Thanks for your help.

Hey I can confirm this issue on a Lenovo E460 with same graphics card but i3 and kubuntu installed. Therefore I assume this is a problem of the graphic card.

Did you find any solution to the problem?

---

### Post by sk1d on 2016-07-28
I found a fix which works for me: [https://github.com/linuxenko/ubuntu-skylake-i915-video-fix](https://github.com/linuxenko/ubuntu-skylake-i915-video-fix)

---

### Post by QDR06VV9 on 2016-07-28
> **sk1d said:**
> I found a fix which works for me: [https://github.com/linuxenko/ubuntu-skylake-i915-video-fix](https://github.com/linuxenko/ubuntu-skylake-i915-video-fix)
Thanks for posting your solution...helps the community.
Kind Regards

---

