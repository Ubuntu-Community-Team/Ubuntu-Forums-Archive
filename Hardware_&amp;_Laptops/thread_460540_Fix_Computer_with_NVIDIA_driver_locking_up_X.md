---
title: "Fix: Computer with NVIDIA driver locking up X"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by OhMyAudi on 2007-05-31
I had a constant issue with my Dell E1505 notebook locking up when i had the nvidia drivers installed.
My hard drive would start chugging away, and evenually the light would go solid.  Then my X session
would completely lock up, leaving me with a blank screen.  If I had been listening to music, the music
would be cut off and I would be left in silence with the last image on my screen prior to lock up.
Sometimes I would be able to move my mouse cursor, sometimes not.  After miles and miles
of forum chatter I discovered that it could be an issue with the NVIDIA drivers that I had installed.
I had always just installed the NVIDIA drivers via synaptic.  Or the Restricted Drivers notifier (Feisty).
So I went into the freenode chat room (#ubuntu) and started asking around.  Someone (I wish I remembered who) gave me this idea and it worked like a charm!

This is assuming you are using a fresh install of UbuntU 7.04



[B][SIZE="4"]***UPDATE***

Simply issue the following command at the terminal:  sudo apt-get remove powernowd

Worked for me.

I will report back in a week[/SIZE][/B]



/*==================  Failed Attempt ====================== */

1)   Have an active connection to the internet

2)   Download the latest driver from the NVIDIA website

3)   Install build-essential from apt/synaptic

4)   Enter command line (CTRL + ALT + F2)

5)   Log in as user, issue "ps -A" without the quotes.  Find Xorg and then issue "sudo kill (PID)" 
      example "sudo kill 4702" once again without the quotes

6)   cd to the location where your NVIDIA-Linux-xxx-xx-x.bin file is - example cd /home/user/Desktop

7)   Issue the command "sudo sh NVIDIA-Linux-xxx-xx-x.bin --no-precompiled-interface"

Let the process run.  At the end it should offer to alter your xorg.conf file for you.

Just accept all the changes and you're done!

If anyone has questions, or maybe I missed something, just let me know.

/*=================================================*/


***UPDATE***

Apparently my method was not full proof.  A couple days after this post, my computer was back to locked up and crap.

Somone please figure this out.  Using windows is driving me mad.

***UPDATE***

I'm going to try disabling powernowd per this article I found: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643)

---

### Post by Tilo on 2007-05-31
yes, that sounds right! 

You may need to type 

     sudo kill -TERM PID

where PID is the process number of X in the left column


You may also need the kernel-sources to do this - i case it complains about missing kernel headers, you need to install the kernel sources , or kernel development package - not sure what the names are in ubuntu

---

