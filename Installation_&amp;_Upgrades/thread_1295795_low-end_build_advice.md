---
title: "low-end build advice"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by mendo on 2009-10-19
i'm about to build an ubuntu server from an old compaq presario desktop.  if all goes well, it will be comprised of:

amd athlon 1400 (thunderbird core)
768 mb ram via 3 sticks of memory - 768 is the max allowed
20gb quantum fireball 4500rpm hd
1tb hd (not sure which one yet)
250 w psu
10/100 pci nic
ati 3d rage pro 2x agp video card
cd burner

-the big drive is going to be sata via pci card - the mobo doesn't have sata support

questions:

1.  should i install the o/s on the old, slow 20gb drive and save the big drive for data, or ditch the old drive all together?

2.  can i even boot from a sata drive that's running off of a pci card?

3. should i install ubuntu 9.04 or xubuntu?  ubuntu, but different version?  what do you think.

4. would it be worth the hassle to max my ram with fewer sticks?  i plan to be running 3x256mb sticks.  should i get a 512 to replace the 256's?  am i nit picking now?

my main concern here is performance for file serving and print sharing.  no gaming/very little browsing - i wanna put this thing in the closet and forget about it.

thanks in advance.  you guys (& gals) are the best

---

### Post by river226 on 2009-10-19
well since your building a ubuntu server i would recommend you go with a pure ubuntu server OS, all command line but it's good terminal practice, and would run plenty faster, as for the HD, depends on the kind of load you are gonna put on this server.

---

### Post by mendo on 2009-10-20
oh yeah - i forgot to mention that - i'm afraid of ubuntu server.  i would like to get this running next week and i can only use terminal commands, it prob won't happen.  maybe i'll give it a whirl...

there won't be much of a load on this pc.  it's for home use.

anyone else?

---

### Post by Paul41 on 2009-10-20
I have a similar set up to you and use Ubuntu server. It was easy to set up. I had mine set up in a day and it was also my first time with a command line only server. I have 4 computers connecting to mine and also serve up music with firefly and speed is never a issue (I have the same amount of RAM).

---

### Post by K.Mandla on 2009-10-20
> **river226 said:**
> well since your building a ubuntu server i would recommend you go with a pure ubuntu server OS, all command line but it's good terminal practice, and would run plenty faster, as for the HD, depends on the kind of load you are gonna put on this server.
If it's only going to boot once and stay online for days, keep the old hard drive as a system drive and leave the other as a data drive. Chances are the difference in performance would be miniscule.

And +1 to the Ubuntu Server ISO. I would even go as far as to suggest something like [FreeNAS]("http://freenas.org/"), if it's going to sit in a closet. Boots to a live environment, is managed through a web page and is rock solid. It might be of more interest to you than setting up and configuring an entire installation.

---

### Post by Mighty_Joe on 2009-10-20
Don't fear the terminal. It's more powerful than you can [imagine]("http://tldp.org/LDP/abs/html/").  Also, pretty much every tutorial and FAQ out there uses terminal commands.  If you don't use a GUI you will be able to use less memory.  I have a home file server (details [here]("http://ubuntuforums.org/showthread.php?t=1244304")) with 512Mb RAM and if I weren't running Tomcat (Java web server) I could easily get away with 256Mb.  Less memory = less power consumption.

---

### Post by mendo on 2009-10-20
thanks for all the replies.

i will use the old drive for a system disk and load ubuntu server.

i researched freenas and got really excited until i realized there was no way to share a printer with it.  bummer.

i'm gonna go check out mightyjoe's link right now.

thanks!

i'm still listening if anybody has any tips or links to terminal help that might come in handy.

---

### Post by Mighty_Joe on 2009-10-20
> **mendo said:**
> 
i'm still listening if anybody has any tips or links to terminal help that might come in handy.

There's always Google, but [here]("http://linuxcommand.org/learning_the_shell.php") is a good intro

---

