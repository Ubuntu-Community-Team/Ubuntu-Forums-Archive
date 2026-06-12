---
title: "[SOLVED]  Sigmatel Stac92xx sound trouble"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by mperedithe on 2007-10-21
****Please note that the solution given here is NOT my own work,  others deserve the credit.  This post simply records the steps I personally took that successfully led to getting the sound working on my laptop.  When posted originally I had thought that the following procedure would serve to help others and thus far either it hasn't really helped many or those that have been helped are simply not saying so.  Anyhow, best wishes in your pursuits.***

Hey everyone,
Thought I might post my personal endeavors to get sound working on my laptop.

I have a Gateway NX270 with Ubuntu 6.06LTS that has a Sigmatel sound card.  I studied the posts for over two months and tried various things but the best I could get is a USB set of speakers working.

I would like to thank everyone for their hard work in solving this problem they deserve all the credit as what is shown is not my own.  This post simply serves as a journal of what worked and I thought it would be good to bring it all together since the solution  that worked for me exists in many pieces spread out over many posts.


Open a terminal and enter root with "sudo su" and then entering your password when prompted.

Begin by installing the packages with the following command.  If it does not work the first time then continue on with the other steps and retry before "./hgcompile"

# sudo apt-get install libncurses5-dev gettext libncursesw5-dev speex libspeex-dev liba52-0.7.4-dev libsamplerate0-dev jackd jack-rack libjack0-100.0-dev checkinstall build-essential linux-headers-$(uname -r)

# sudo apt-get install mercurial automake1.4
# mkdir alsa
# cd alsa
# hg clone [http://hg-mirror.alsa-project.org/alsa-driver](http://hg-mirror.alsa-project.org/alsa-driver) alsa-driver
# hg clone [http://hg-mirror.alsa-project.org/alsa-kernel](http://hg-mirror.alsa-project.org/alsa-kernel) alsa-kernel
# cd alsa-driver
# ./hgcompile
# sudo tar zvcf oldsound.tgz /lib/modules/`uname -r`/kernel/sound/*

Then open alsa-base file with the following

# gedit /etc/modprobe.d/alsa-base

and add the following two lines at the bottom then save and close the file

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1

before exiting and restarting the PC I strongly suggest that you write down the following code and keep it by your side.  Occasionally while trying to get my sound working I would lose my GUI desktop.  The following can be entered into the terminal either before restarting or after to regain your GUI desktop.

# sudo apt-get install gdm ubuntu-desktop

That's it.  I hope this information is helpful.  If some of the instructions seem odd or confusing you can find them in various posts by searching "gateway laptop no sound".

Thanks again to everyone for their hardwork.  This is why I love linux.

---

### Post by dhubbard on 2007-11-09
Thanks for posting this, but I didn't have any luck with it. I'm using a Gateway MT3705, with a STAC92xx sound card. I followed your instructions, but I still can't get the sound to work. I'm not getting any errors during the process.

Using Kubuntu Dapper.

Any advice would be appreciated.

---

### Post by mperedithe on 2007-11-10
Sorry to hear that it didn't work for you.  You might search the other posts--particularly the older ones.  Instructions vary and there may be a line that didn't work for me that might work for you.

---

### Post by lvleph on 2007-12-04
> **dhubbard said:**
> Thanks for posting this, but I didn't have any luck with it. I'm using a Gateway MT3705, with a STAC92xx sound card. I followed your instructions, but I still can't get the sound to work. I'm not getting any errors during the process.

Using Kubuntu Dapper.

Any advice would be appreciated.

[Try this.](http://donnieknows.com/bin/view/Main/GatewayML3109) It worked for me up through Feisty. Does not work in Gutsy. Still trying to figure out why.

---

