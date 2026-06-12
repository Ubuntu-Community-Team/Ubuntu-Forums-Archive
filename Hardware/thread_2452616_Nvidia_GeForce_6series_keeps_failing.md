---
title: "Nvidia GeForce 6series keeps failing"
date: 2020-10-25
forum: Hardware
---

### Post by rhudsonsamuel on 2020-10-25
Hi,
Am using Ubuntu for more than 5years in laptop
I now tried to install in my old AMD pc (phenom 550) with GeForce 6150SE (Nvidia 430)..#desktop
I tried different versions from 16.04 to 20.04
In everything I faced one issue (Nvidia driver) 
Only 16.04 has Nvidia driver support but while installing via (additional drivers) ended in issue and submitted the report and finally found many are facing it #screentearing
After 16 there are no new update (304 driver) and am forced to use default nouveau driver ..
It won't be a problem if nouveau works fine
But am facing issues like screen tearing
And sometime I can see gridlines all over my desktop screen (ended no mouse and keyboard working)
Only way is to force reboot
Anyone help me please

---

### Post by mastablasta on 2020-10-26
this is the part that sucks with nvidia. just dropping support and not at least offering some help to nouveau people or better yet open souring the old driver.

anyway, check the nouveau driver pages ( [https://nouveau.freedesktop.org/](https://nouveau.freedesktop.org/) ). perhaps there is a switch that can help you regulate the card. I know that AMD had plenty kernel switches that could be used. also you might have to move to org session (check if you are running that or if wayland is set) 

you may nee dot manually enable vsync using xorg file.

maybe this offers a clue?: [https://ubuntuforums.org/showthread.php?t=2362982](https://ubuntuforums.org/showthread.php?t=2362982)

---

