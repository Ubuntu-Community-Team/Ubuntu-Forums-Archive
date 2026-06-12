---
title: "Samsung Notebook 7 Force with headphone jack and HDMI output issues on 19.10"
date: 2019-10-28
forum: Hardware
---

### Post by wowbaggerbr on 2019-10-28
Guys, I just bought this machine ([Samsung Notebook 7 Force]("https://www.samsung.com/us/computing/windows-laptops/notebook-series-7/notebook-7-force-np760xbe-x01us/") or Style S51 Pro on some regions) and I'm in need of some help: some hardware isn't working properly on 19.10, even on a rolling distro like Manjaro. I want to learn how to debug this and I want to help the development community, but I don't really know how to do it or where should I start. I know of another user of this machine facing the same issues and I [recently stumble upon this case]("https://askubuntu.com/questions/1184206/asus-zenbook-jack-problem/1184216#1184216"), which seems very similar, but with another laptop (although the hardware is similar, being an eight generation Intel platform on both cases).

So far, I found two major issues:

- Headphone output won't work. I've checked alsamixer and nothing is muted. With pavucontrol I can see that the system detects that there is a headphone connected. If I bump the volume to the stratosphere, I can hear something veeeeery faint and heavily distorted being played, like a buzzing effect over the actual sound.

- HDMI output also doesn't work. The system detects the HDMI event, when I plug the cable, and shows me the video output dialog on Kubuntu 19.10, but it simply doesn't display anything on the TV and monitor that I've tried so far, regardless of what mode I choose. [Both those issues happen to the other guy with the same laptop]("https://forums.linuxmint.com/viewtopic.php?f=49&t=303303") (in the link he reports only the HDMI, but I got in touch with him and the headphone jack is reproductible on his computer as well).

I've tested both issues on Kubuntu 19.10 and Manjaro KDE (the latest one). Needless to say that both, heaphone and HDMI output, work fine on Windows.

I'm thinking this is some unsupported hardware quirk, but I don't know how to debug this, document it and file the issue so that developers can fix it. Any light on this would be greatly appreciated.

---

### Post by akicay on 2019-11-10
I found solution for this problem. Solution is for other Linux distribution but I think it's similar for Ubuntu. [[https://forum.manjaro.org/t/solved-ryzen-7-with-gtx1660ti-driver-problem-black-screen-before-login/107633](https://forum.manjaro.org/t/solved-ryzen-7-with-gtx1660ti-driver-problem-black-screen-before-login/107633)]

---

### Post by robsontenorio on 2020-03-29
Headphone jack 

[https://www.linux.org/threads/samsung-notebook-7-force-headphone-jack-and-keyboard-lighting-issues.27304/#post-87920](https://www.linux.org/threads/samsung-notebook-7-force-headphone-jack-and-keyboard-lighting-issues.27304/#post-87920)

---

