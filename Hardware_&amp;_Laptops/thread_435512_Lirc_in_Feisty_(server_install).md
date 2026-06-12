---
title: "Lirc in Feisty (server install)"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by stefansjs on 2007-05-07
Well, as most people who use ubuntu (i think) I am trying to get mythtv to work.  In this case mythtv is fully configured (thank you to whomever set up the package on the repositories to automatically set up everything!), and I am trying to get LIRC to work with it.  As far as I can tell, there are primarily two sets of instructions (and their derivitaves) on the internet.  The first is this one:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)
and the other one:
[http://ubuntuforums.org/showthread.php?t=288229](http://ubuntuforums.org/showthread.php?t=288229)
which involves compiling and building from source.  The latter doesn't work because it complains about a missing directory when i try to make.  Can't figure out what's supposed to be there.  The former seems to work the whole time until I try to:
```
sudo /etc/init.d/lirc start
```
According to the documentation it's supposed to "hang" and when I press a button on the remote then it displays things.  However it just does this:
> stefan@stefan-fast:/etc/lirc$ sudo /etc/init.d/lirc start
Password:
Starting lirc daemon: lircd.
stefan@stefan-fast:/etc/lirc$ 
I took a look at dmesg and the only error that i can see that appears relevent is:
> [   65.106900] lirc_gpio: no version for "lirc_unregister_plugin" found: kernel tainted.
However it later says:
> [   65.119313] lirc_gpio (-1): card type 0xd, id 0x41461
[   65.140796] lirc_dev: lirc_register_plugin: sample_rate: 10
[   65.143318] lirc_gpio (0): driver registered
I also see encouraging things like 
> [   53.043216] bttv0: detected: AVerMedia TVCapture 98 [card=13], PCI subsystem ID is 1461:0004
[   53.043221] bttv0: using: AVerMedia TVCapture 98 [card=13,autodetected]
[   53.043267] bttv0: gpio: en=00000000, out=00000000 in=00e47ff3 [init]
[   53.045758] bttv0: Hauppauge/Voodoo msp34xx: reset line init [11]
[   53.076390] bttv0: Avermedia eeprom[0x4001]: tuner=2 radio:no remote control:yes
[   53.076398] bttv0: using tuner=2


Somebody please help me.  Does feisty do something to lirc that it terminates immediately?  Is lirc working for me and I just don't realize it?
thanks

---

### Post by newlinux on 2007-05-07
I believe it is supposed to "hang" after you run irw, not right after you start LIRC.

So after you have started LIRC with the command you used above type:

```
irw

```

at the command line and then try the remote. If it doesn't hang something is wrong with the module you need for your remote, or you may have not loaded it or loaded the wrong one...

---

