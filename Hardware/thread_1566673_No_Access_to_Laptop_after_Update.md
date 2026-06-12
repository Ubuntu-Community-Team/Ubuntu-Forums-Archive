---
title: "No Access to Laptop after Update"
date: 2010-09-02
forum: Hardware
---

### Post by klafilin on 2010-09-02
Hello All, 
I was working with my Laptop,Compaq Presario CQ42, the Update Manager popped up with new Updates and I updated the Laptop.After Restart I got only to a Screen with the Message "udevadm trigger
is not permitted while udev is uncofigured". I am using Ubuntu
10.04LTS. I am a complete Newby and dont know what to do. 
Could anyone please help me and explain in simple Terms how to solve the Problem???

---

### Post by Fafler on 2010-09-02
Try this: [https://bugs.launchpad.net/ubuntu/karmic/+source/apt/+bug/453678/comments/10](https://bugs.launchpad.net/ubuntu/karmic/+source/apt/+bug/453678/comments/10)

---

### Post by klafilin on 2010-09-02
Hi Fafler,thanks for your Reply! I gave it a go, but it doesn't 
work for me. When I press "shift" during bootup, nothing happens 
and I get the same Message as before. When I press "Esc" during 
bootup my Laptop only gives me the Choice to boot from Hard-Disc
or from DVD-Drive. Is it possible to do something from a Live-DVD?

---

### Post by Fafler on 2010-09-03
Yet. It should be possible to boot from live CD, mount filesystem, chroot to it and run the command that fixes the broken udev, but i can't remember the exact procedure from the top of my head.

---

