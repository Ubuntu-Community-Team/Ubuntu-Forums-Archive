---
title: "SIR IrDA problem kubuntu 7.04"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by jnedbal on 2007-04-26
Dear All,

I have ASUS A3Ac notebook with integrated IrDA. I have been using OpenSuSE 10.2 with 2.6.18.8 and then 2.6.21-rc7-43 kernel. IrDA under OpeSuSE worked out of the box starting it with YaST or just a simple command [COLOR="RoyalBlue"]irattach /dev/ttSy1 -s[/COLOR].

Unfortunately, I am not able to get it working with Kubuntu 7.04 kernel 2.6.20-15.
[COLOR="RoyalBlue"]
lsmod | grep ir[/COLOR] gives

[COLOR="Red"]ircomm_tty             39560  0
ircomm                 23684  1 ircomm_tty
irtty_sir               9600  0
sir_dev                17156  1 irtty_sir
irda                  201276  4 ircomm_tty,ircomm,irtty_sir,sir_dev
crc_ccitt               3072  1 irda[/COLOR]

This means that all the modules related to IrDA that were loaded in the OpenSuSE system are also loaded in the Kubuntu system.

But when I try [COLOR="RoyalBlue"]irattach /dev/ttSy1 -s[/COLOR] i get and check [COLOR="RoyalBlue"]tail /var/log/messages[/COLOR] I get following:
[COLOR="Red"]
Apr 27 00:06:13 A3Ac irattach: Stopping device /dev/ttyS1
Apr 27 00:06:13 A3Ac irattach: ioctl(SIOCGIFFLAGS): No such device
Apr 27 00:06:13 A3Ac irattach: exiting ...
Apr 27 00:06:13 A3Ac kernel: [ 8473.668000] ttyS1: LSR safety check engaged![/COLOR]

In OpenSuSE the IrDA hardware gets attached and I can see that irattach is a running process and [COLOR="RoyalBlue"]irdadump[/COLOR] lists the activity. This is not true in my Kubuntu system. irattach is not loaded as can be seen from applying the following command [COLOR="RoyalBlue"]ps -e | grep ir[/COLOR] which produces:

[COLOR="Red"]    3 ?        00:00:00 ksoftirqd/0
 3589 ?        00:00:00 irda_sir_wq
 6295 ?        00:00:15 firefox-bin[/COLOR]

obviously when I try [COLOR="RoyalBlue"]irdadump[/COLOR] I don't get any response.

Googling the phrase [COLOR="Olive"]LSR safety check engaged![/COLOR] did not help me. I could just understand that there is something wrong with the way the hardware is handled by the system but I could not find any solution or hint.

There is one more interesting aspect to it. I can do [COLOR="RoyalBlue"]irattach /dev/ttSy0 -s[/COLOR] and attach the COM port. I even get output from [COLOR="RoyalBlue"]irdadump[/COLOR], It's just useless because it's not the correct port.

[COLOR="RoyalBlue"]dmesg | grep tty[/COLOR] gives following:

[COLOR="Red"][   17.695347] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.695487] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.696046] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   48.736000] ttyS1: LSR safety check engaged!
[   48.736000] ttyS1: LSR safety check engaged!
[   61.636000] ttyS1: LSR safety check engaged!
[  563.388000] ttyS1: LSR safety check engaged!
[  616.296000] ttyS1: LSR safety check engaged!
[  994.636000] ttyS1: LSR safety check engaged!
[ 1030.368000] ttyS1: LSR safety check engaged!
[ 2152.308000] sirdev_get_instance - ttyS0
[ 2152.308000] irtty_open - ttyS0: irda line discipline opened
[ 2257.456000] ttyS1: LSR safety check engaged!
[ 2283.404000] irtty_close - ttyS0: irda line discipline closed
[ 2287.132000] ttyS1: LSR safety check engaged!
[ 8473.668000] ttyS1: LSR safety check engaged!
[ 8933.188000] ttyS1: LSR safety check engaged!
[ 8933.188000] ttyS1: LSR safety check engaged![/COLOR]

Any idea what's wrong?

Any help greatly appreciated.

jakub

---

### Post by jnedbal on 2007-06-09
Hi guys,

My post has been hanging around for a while without a response. But I discovered a new thing which could provide some clue to any of you and you might help me tracking down the problem.

If I boot the LIVE CD and install irda-utils. I am able to irattach and get my irda working. If I make a fresh install of ubuntu I am able to do the same thing. My irda works perfectly.

Then I restart my computer and suddenly it gives this LSR: safety check engaged. and the IrDA is not working. DO you have any idea why this happens and how can I use this 
'feature' to track down what has changes between the first boot of the system and any later boot? It must be some little stupid bug which is easy to find and solve, but I have no idea how to approach it. Also it is very hard to try because the only time it works is after a fresh reinstall of the system which is really annoying and hard to work with.

Thanks for you thinking time. Any help will be appreciated.

jakub

---

### Post by dcomsa on 2007-06-15
Hi jnedbal,

Unfortunately I don't have a solution to your problem. But I do have your problem. About a week or two ago I have managed to get the infrared port going. Yesterday I tried again to connect my phone to my laptop but the ir port doesn't work any more. I really don't know what's going on. I have the same laptop model as yours.

If I'll find something, I'll let you know.

Br,
Daniel.

---

### Post by shadwstalkr on 2007-08-16
I'm having the same problem with my laptop in Kubuntu 7.04.  Have you reported this as a bug?  I haven't seen the information about a clean install before, so that could be very useful to whoever is working on this bug.

---

