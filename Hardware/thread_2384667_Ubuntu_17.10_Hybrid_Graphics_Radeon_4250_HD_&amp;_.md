---
title: "Ubuntu 17.10 Hybrid Graphics Radeon 4250 HD &amp; 5650 HD"
date: 2018-02-10
forum: Hardware
---

### Post by xviravenivx on 2018-02-10
So I have tried for almost three weeks to get it to where I can switch graphics cards but have not been able to. I have searched google and Ubuntu forums and have not found a thing relating to the hardware in my laptop. My current laptop I am stuck using since my Acer finally died is an HP Pavilion DV6-3160US, my issue is trying to use my discrete graphics (5650 HD) to test dolphin (there are other things i want to do as well but thats the main one), yet even using the&nbsp; the ubuntu help page towards hybrid graphics I have gotten no where ([https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)). In things I have found on google include a posts that say downloading the official drivers from AMD but the 4250 isnt supported and suggest using the drivers included in ubuntu ([https://askubuntu.com/questions/730110/problem-with-dual-amd-graphics-card-amd-radeon-r5-a8-and-radeon-r7-m260?rq=1]](https://askubuntu.com/questions/730110/problem-with-dual-amd-graphics-card-amd-radeon-r5-a8-and-radeon-r7-m260?rq=1])), or adding "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.runpm=0" " to the grub ([https://askubuntu.com/questions/648426/discrete-graphics-always-dynoff&nbsp;](https://askubuntu.com/questions/648426/discrete-graphics-always-dynoff&nbsp;) [Did not try the second option because I am hoping to switch between the two, even now with the 5650 HD stuck in dynoff i get 46 minutes of battery life])

Output of cat switcheroo
0:IGD:+:Pwr:0000:01:05.0
1:DIS: DynOff:0000:02:00.0
2:DIS-Audio: :Off:0000:02:00.1

Everything I have tried has ended in that same output, please if any of you have any advice it would be appreciated

---

