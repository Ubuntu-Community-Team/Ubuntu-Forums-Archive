---
title: "cman question"
date: 2009-04-14
forum: Hardware
---

### Post by drummerchrissk on 2009-04-14
I recently installed Ubuntu on my Compaq Armada E500. Everything worked fine (and really still works fine, my question is aimed more at solving something that's become an annoyance) One night I was trying to install the Windows program Guitar Pro 5 on my system via the CD. Me, being new to Ubuntu did not know yet that after a CD has been inserted in the drive, you cannot open your CD drive by merely pressing the button. You must eject the CD via Nautilus. Anyways, long story short, the install wasn't working, I wanted to get my CD, it wouldn't let me, so I found a needle and forced the drive open. Then as I recall (this was a few months ago that this happened, I've been dealing with this for quite awhile now) my system froze completely, forcing me to do a hard reboot. When I boot my system back up I see normal screens until the Ubuntu load bar. It gets maybe 50-60 percent of the way full and then jumps to a screen reading this...

>     Starting daemons: groupd fenced dim_controld gfs_controld
    Joining fence domain:groupd[4207] : cman_init error 2

fenced[4210] : cman_admin_init error 2

dim_controld[4207] : cman_admin_init error 2

gfs_controld[4211] : cman_admin_init error 2

fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
CCS[4183]: [CCS ] Unableto connect to cluster infrastructure after 30 seconds.

fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
CCS[4183]: [CCS ] Unableto connect to cluster infrastructure after 60 seconds.


fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
CCS[4183]: [CCS ] Unableto connect to cluster infrastructure after 90 seconds.

so on and so forth until it reads


> fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
CCS[4183]: [CCS ] Unableto connect to cluster infrastructure after 300 seconds.

Then it reads something like this.

fence tool timed out waiting for cluster quorum to form

Now I can bypass all of it when I see 'fence_tool: waiting for cman to start' by pressing Control+Alt+Delete. It then bypasses the long wait, finishes loading the system, and delivers me to my login screen.

My question is what caused this and how do I get rid of it. As I said, I've been dealing with this for quite sometime now and I've finally grown tired of it.

I posted this forum here in the Hardware and Laptop section solely based on the fact that I'm using a laptop and I'm not really sure if the problem I'm having directly relates to laptops or not.

Please help!

---

### Post by WhenChaosReigns on 2009-06-22
It will eventually time out after more than 300 seconds. When it does it will allow you to log in as you normally do. Once you are logged in, go to:

System
     Administration
          Synaptic Package Manager

It will prompt you for your root password. Enter the root password. On the right hand side under package, scroll down until you see "cman" highlight it, and select it to be uninstalled. 

Hit Apply, once it is uninstalled, your problem with cman will go away.

---

### Post by drummerchrissk on 2009-06-23
Thank you. The problem is fixed now. : )

---

