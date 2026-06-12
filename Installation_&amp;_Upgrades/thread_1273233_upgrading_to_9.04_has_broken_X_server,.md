---
title: "upgrading to 9.04 has broken X server,"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by frazerr on 2009-09-23
I was updating from 8.10 to 9.04

It said the update failed and supposedly reverted to 8.10, but it looks like nothing reverted.

firefox crashed on opening and sudo seg faulted so I restarted
and on booting it reported the Xserver would not start,
so now I have only a terminal...  

after rebooting failed I went in to the recovery kernel,
and told it to fix broken packages.
This took a few hours but seemed to make no difference.

oh, I just noticed my kernels are still ubuntu 8.10 
perhaps someone could tell me how to update them?


the update did not go smoothly,
saying some packages could not be installed,
and when I clicked ok, it said those packages were already installed.
After that happened a few times I stopped keeping track.

I have included the X log  and the dist-upgrade logs

in the attached zip file there is
x.0.log

and from /var/log/dist-upgrade:
  main.log.partial
  20090922-1713/
      main5pm
      apt5pm
  20090923-0441/
      main4am
      apt4am





so yes, this is an update bug, but it has also rendered my computer useless to me,
so any help would be appreciated.

I have an eeepc 901
I can get to a terminal

help...  please

---

### Post by Lars Noodén on 2009-09-23
What version does this give ? [INDENT]lsb_release -rc[/INDENT] 
Does it match what is in the sources file? INDENT/etc/apt/sources.list[/INDENT] ?

And these give no errors?
[INDENT]
 sudo apt-get update
 sudo apt-get dist-upgrade [/INDENT]

---

### Post by frazerr on 2009-09-25
Hi Lars,

thanks for your help.

so, heres my answers:

[B]What version does this give ?
    lsb_release -rc
[/B]
8.10
intrepid

[B]Does it match what is in the sources file?
/etc/apt/sources.list?
[/B]
no.  the source file is all jaunty repositories


so I assume running apt-get update is not such a good idea.

what next?


thanks in advance for your help.

---

### Post by frazerr on 2009-09-25
oh,

also when I log in I get this:

-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied


and each time I log in,
I get more and more of them.

today there seemed to be about 2 screens full

---

### Post by Jimmyfj on 2009-09-25
If you are able to login to your system as a regular user then after login your change to root:

```
sudo su
```

Once in root-mode you type in this command:

```
dexconf
```

This should set your graphics driver back to the Vesa-driver.

---

### Post by Lars Noodén on 2009-09-26
> **frazerr said:**
> oh,

also when I log in I get this:

-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied


and each time I log in,
I get more and more of them.

today there seemed to be about 2 screens full

It seems that much more than the X server is broken.

---

### Post by frazerr on 2009-09-27
any idea why there are more and more

-bash: /dev/null: Permission denied

each time I log in?

today it displayed 
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
...
and kept streaming pages of them for about 2 seconds.

running dexconf changed nothing in my xorg.conf file.

I ran
sudo apt-get update

but it could not resolve any of the archives,
so I guess wireless networking is not working.

any idea how to get wireless networking going just from the command line?

or if I go and buy a network cable, will that work?

---

### Post by wojox on 2009-09-27
Try and remove and recreate it:

```
sudo rm /dev/null
sudo mknod -m 0666 /dev/null c 1 3
```

---

### Post by frazerr on 2009-09-27
ok, I went and got a network cable.

I tried lynx and got
File "/USR/LIB/COMMAND-NOT-FOUND", LINE 8, IN <MODULE>
   IMPORT cOMMANDnOTfOUND
iMPORTeRROR: nO MODULE NAMED cOMMANDnOTfOUND


I tried pinging some addresses and the network is unreachable


so, I have no networking, and every thing seems broken.

I am going traveling in a few days,
and need a working computer with me.
so any advice would be appreciated.

---

### Post by frazerr on 2009-10-02
Lars,

can you please suggest the next steps for me to take.

not having a computer really sucks

---

