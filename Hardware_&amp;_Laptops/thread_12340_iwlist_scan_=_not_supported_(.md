---
title: "iwlist scan = not supported :("
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by ming0 on 2005-01-23
I've got a linksys wpc11 v.3 (which is a prism chipset that uses orinoco drivers) pcmcia wifi card for my laptop, and get the follwing error:

```
dean@lappy:~$ iwlist eth1 scan

eth1        Failed to read scan data: Operation not supported
```
Does anyone have any recommendations for inexpensive 802.11b (or b/g) cards that are automatically supported in ubuntu that support iwlist scan?

If you know of a place to get one for cheap, you could post that info too :)

Thanks!

---

### Post by ceekay on 2005-01-24
Do you really need it to automatically work in ubuntu? It's not that hard to install drivers that support scanning... You can grab the drivers from here:
[http://www.nongnu.org/orinoco/](http://www.nongnu.org/orinoco/)
Just download the tar.gz, then:

switch to root:
sudo su

stop the pcmcia card for now so it unloads the drivers:
cardctl eject

unpack and install the drivers:
tar zxf orinoco-0.15rc2.tar.gz
cd orinoco-0.15rc2
make
make install

this will drop the modules you need in /lib/modules/2.6.x/kernel/drivers/net/wireless where x is your kernel version, so you will probably want to do a 

cp /lib/modules/2.6.x/kernel/drivers/net/wireless/* /lib/modules/2.6.x-y-386/kernel/drivers/net/wireless

to copy the new modules over (there may be a better way to do this, like getting the make file to output to the right place, anyone know?). y is the kernel revision you are running. 

now put your card back in and it should load the scanning-supported drivers. =)


If the make doesn't work to begin with, make sure you have downloaded the linux-source package for the version you are running. I will assume you are running 2.6.8.1, but just change the versio number if you aren't. Once you download it:

sudo su
cd /usr/src
tar zxf linux-source-2.6.8.1.tar.gz
ln -s /linux-source-2.6.8.1 linux
cp /boot/config-2.6.8.1-y-386 /usr/src/linux/.config       (where y is your kernel revision- either 3 or 4 on warty)
cd linux
make

It will take a little while to compile everything. Compiling shouldn't be necessary, but for some reason, I have found that the orinoco modules won't compile otherwise.

Now compile the modules!

---

### Post by ming0 on 2005-01-24
I didn't know that this was an option--but it'll be great if I can get it going... I did need to get the kernel source and I compiled it as per your instructions, but once I am able to compile the orinoco modules, I get a bunch of warnings, and then it dies! 

```
 root@lappy:/home/dean/Desktop/orinoco-0.15rc2 # make
make -C /usr/src/linux-headers-2.6.10-2-686 M=/home/dean/Desktop/orinoco-0.15rc2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-2-686'
  CC [M]  /home/dean/Desktop/orinoco-0.15rc2/hermes.o
In file included from /home/dean/Desktop/orinoco-0.15rc2/hermes.c:54:
/home/dean/Desktop/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/home/dean/Desktop/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/dean/Desktop/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':

**I DELETED A THOUSAND OR SO LINES OF SIMILAR WARNINGS HERE**

  CC [M]  /home/dean/Desktop/orinoco-0.15rc2/orinoco_nortel.o
In file included from /home/dean/Desktop/orinoco-0.15rc2/orinoco_nortel.c:67:
/home/dean/Desktop/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/home/dean/Desktop/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arguments to function `pci_save_state'
/home/dean/Desktop/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_resume':
/home/dean/Desktop/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arguments to function `pci_restore_state'
make[2]: *** [/home/dean/Desktop/orinoco-0.15rc2/orinoco_pci.o] Error 1
make[1]: *** [_module_/home/dean/Desktop/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-2-686'
make: *** [modules] Error 2 
```

So do you know what is wrong? Maybe we can ask the devs to just put the latest orinoco drivers into their kernel? 

Thanks a bunch for the help :)

---

### Post by andy_sp1ke on 2005-01-27
this is the same problem i i have just hit with a DLINK DWL G650 pcmcia card, it comes up at athero and ath0 but i am not sure what module it loads. i can use it an connect to a network if i know its essid so at home thats fine as i know whats its called. I cant scan though, i get the same error as you do. I dont really understand the way the hardware for this works as to where and when the modules are loaded, where u get them and how u change whats loaded :s

andy

---

### Post by ceekay on 2005-01-31
note- you need the linux-source package... not the kernel headers- these are NOT the same thing. It looks like you are using the headers.

---

### Post by TheOtherShoe on 2005-02-21
I was getting the same compiler errors as ming0, even after following all the suggestions in this thread. I also definitely made sure that the orinoco driver was building against the kernel source and not the kernel headers. The only way I could get the driver to compile was to modify the driver code to fix the last two compiler errors. There is probably a better way to fix this problem, but I am at a loss as to what that might be. Here is a patch of the changes I made in case it helps anyone:
```
diff -Naur orinoco-0.15rc2/orinoco_pci.c orinoco-0.15rc2-patched/orinoco_pci.c
--- orinoco-0.15rc2/orinoco_pci.c       2005-02-20 21:38:56.494893376 -0800
+++ orinoco-0.15rc2-patched/orinoco_pci.c       2005-02-20 21:39:09.226957808 -0800
@@ -327,7 +327,7 @@

        orinoco_unlock(priv, &flags);

-        pci_save_state(pdev, card->pci_state);
+        pci_save_state(pdev);
        pci_set_power_state(pdev, 3);

        return 0;
@@ -344,7 +344,7 @@
        printk(KERN_DEBUG "%s: Orinoco-PCI waking up\n", dev->name);

        pci_set_power_state(pdev, 0);
-        pci_restore_state(pdev, card->pci_state);
+        pci_restore_state(pdev);

        err = orinoco_reinit_firmware(dev);
        if (err) {
```
So far the driver seems to be working fine; although I haven't messed around with suspending the card, which is what the functions I modified control. I will report back if this ends up causing my card to explode or anything like that  :wink:

---

### Post by mr_ed on 2005-02-21
You may want to try "sudo iwlist scan"

---

### Post by TheOtherShoe on 2005-02-21
Yep, scanning works. Even with my crazy tinkering. Here is the output:
```
hallettj@atreus ~ $ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:02:2D:1D:3C:B0
                    ESSID:"Reedwlan"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:-55 dBm  Noise level:-88 dBm
                    Encryption key:on
```
I am now a happy user :D

I also tried disabling and re-enabling my card using cardctl eject and cardctl insert. I don't know if this makes use of the pci suspend and resume functions, but it seems to work.

---

### Post by ming0 on 2005-02-21
[QUOTE=TheOtherShoe]Reedwlan[/QUOTE]

Do you go to Reed? I've got a few friends who went there :)

---

### Post by TheOtherShoe on 2005-02-21
Yes I do, and that is pretty awesome!

---

### Post by NTolerance on 2005-05-12
Can someone post a complete how-to on getting scanning to work with an Orinoco card?  I am glad to see what's been posted already, but I am weary of trying this until there are more details.  I am running Hoary with a card that uses the orinoco_cs drivers.  Thanks.

---

### Post by ninotob on 2005-06-28
[QUOTE=TheOtherShoe]I was getting the same compiler errors as ming0, even after following all the suggestions in this thread. I also definitely made sure that the orinoco driver was building against the kernel source and not the kernel headers. The only way I could get the driver to compile was to modify the driver code to fix the last two compiler errors. There is probably a better way to fix this problem, but I am at a loss as to what that might be. Here is a patch of the changes I made in case it helps anyone:[/QUOTE]

Confused here -- I've never messed with kernel module compiling before a week ago.  Anyway, I get the same error as mentioned above.  I'm not sure how to make sure I'm compiling against the source or the headers.  I did follow the excellent howto on compiling drivers to make kismet work, and I succesfully accomplished that.  I'm also not entirely clear on how to use the patch.  I did this in the dir with the orinoco source:

[INDENT]*patch -p1 --dry-run < ./pat*[/INDENT]

(I named the patch "pat").  Anyway, it gives me an error:
[INDENT][I]
Hunk #1 failed at 327.
Hunk #2 failed at 344.
2 out of 2 hunks FAILED -- saving rejects to file orinoco_pci.c.rej[/I][/INDENT]
 
Because of the error - I never applied the patch.

Questions:
--how do I double check I'm compiling against the source, not the headers?
--I've done apt-get for these files:
[list]
[*]linux-headers-2.6.10-5-386
[*]linux-headers-2.6.10-5
[*]linux-source-2.6.10
[*]build-essential
[/list] 

Are these wrong?

I created the link in /usr/src (linux -> /usr/src/linux-source-2.6.10).
I actually reinstalled the source after failing the first time thinking that patching for kismet might mess up things -- so the source is fresh and clean.

I figure I did the kismet stuff right because I can scan networks.  It's just that iwlist doesn't work and I really want it to so I can use gtkwifi with all the cool features.

Please point out where I'm going wrong.  Thank you

---

### Post by andyanderso on 2006-04-23
I also have a WPC 11 ver. 3 wirless card and whenever I try to iwlist scan, I also get a message saying that eth1 (my wireless card) does not support scanning. I have looked through the forums and only found one possible fix so far and that is here

However when I go to try it after I type the make command I get this message:

[FONT="Courier New"][COLOR="Blue"]root@hermes:/home/andy # cd Desktop/orinoco-0.15rc4
root@hermes:/home/andy/Desktop/orinoco-0.15rc4 # make
Makefile:8: *** Kernel tree not found - please set KERNEL_PATH.  Stop.
root@hermes:/home/andy/Desktop/orinoco-0.15rc4 # make install
Makefile:8: *** Kernel tree not found - please set KERNEL_PATH. Stop.[/COLOR][/FONT]

maybe someone can help me with using "makefile." As I am obviously not very good with it....

Please help!

andy

---

