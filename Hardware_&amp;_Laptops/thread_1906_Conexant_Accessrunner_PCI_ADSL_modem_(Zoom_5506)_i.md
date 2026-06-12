---
title: "Conexant Accessrunner PCI ADSL modem (Zoom 5506) installation?"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by joseywales72 on 2004-10-24
I need to make this modem to work in Ubuntu. I have tried numerous sources on the net but couldn't get it to work.
Any ideas?
I have the conexant drivers from madhouse.co.uk, and how to from [http://www.unixhead.org/docs/conexant/linux-conexant-howto.html](http://www.unixhead.org/docs/conexant/linux-conexant-howto.html)
but no use. 
I know it is my incompetency but... Resources on the net are somewhat confusing...
Help.
Thank you.

---

### Post by xpic on 2004-11-28
[QUOTE=joseywales72]I need to make this modem to work in Ubuntu. I have tried numerous sources on the net but couldn't get it to work.
Any ideas?
I have the conexant drivers from madhouse.co.uk, and how to from [http://www.unixhead.org/docs/conexant/linux-conexant-howto.html](http://www.unixhead.org/docs/conexant/linux-conexant-howto.html)
but no use. 
I know it is my incompetency but... Resources on the net are somewhat confusing...
Help.
Thank you.[/QUOTE]

I'm using  a PCI AccessRunner with ubuntu just now. :wink:  

So I try to help you now. Let me know if instruction are enough. 

You my find the driver in this guide.
[http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html#r](http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html#r)

But Ubuntu installation is different. 

This is the steps that I follow.

I use only this package from that guide. 
[http://patrick.spacesurfer.com/adsl/CnxADSL-6.1.2.007-PIM-2.6-1.1.tar.bz2](http://patrick.spacesurfer.com/adsl/CnxADSL-6.1.2.007-PIM-2.6-1.1.tar.bz2)
I suppose to unpack in /root 

To compile it you need the kernel headers. Chose it from Synaptic. Pay attention to choose the header of your kernel. 
I use the linux-headers-2.6.8.1-3-k7

Download and unpack this source: 

Now you need a link to your source because the driver look for /usr/src/linux and ubuntu uses /usr/src/linux-headers-2.6.8.1-3-k7. or 
Example: 
$ ln -s /usr/src/linux-headers-2.6.8.1-3-k7 /usr/src/linux

Now return to the source dir. 

$ cd /root/CnxADSL-6.1.2.007-PIM-2.6-1.1

Build the Makefile running configure. 
$ ./configure

Build the driver with make. 
$ make 
......

Don't use make install from this but. 
$ cd DownLoadApp  
Exec make install 
$ make install 

Now configuration is in /etc/Conexant 

You need the module. So 
$cd ../KernelModule
$mv  CnxADSL.ko /lib/modules/2.6.8.1-3-k7/kernel/net/atm/CnxADSL.ko
Now you need to update module dependences. 
$depmod

Now copy the initscript in the /etc/init.d with the name cnsadslctl 

This is my script.
----------------------------------------------------------------------------
#!/bin/bash
# Modified by Patrick Mackinlay (SpaceSurfer Ltd.)
#  [email]patrick@spacesurfer.com[/email]
#
# chkconfig: 345 09 91
# description: This is the boot/shutdown script for the Conexant AccessRunner
#              ADSL modem.

# Source function library.
#. /etc/init.d/functions

# See how we were called.
case "$1" in
  start)
      # if the driver is not already loaded then
      # Load the module

      if [ ! -f /var/lock/subsys/cnxadslctl ]; then
         echo " Starting AccessRunner      "
         modprobe pppoatm
         modprobe CnxADSL                   \
             CnxtDslVendorId=0x14F1         \
             CnxtDslArmDeviceId=0x1610      \
             CnxtDslAdslDeviceId=0x1611     \
             CnxtDslPhysicalDriverType=1

         # Initialize the firmware and start training
#         echo "Download Starting."
         /etc/Conexant/cnxadslload /etc/Conexant

         RETVAL=$?
         if [ $RETVAL -eq 0 ] ; then
            touch  /var/lock/cnxadslctl
            /usr/sbin/pppd
         fi
      else
         echo -n "AccessRunner already loaded"
      fi
      echo
      ;;

  stop)

      PPPUP=`ps aux | grep -v grep | grep pppd`
      if [ -n "$PPPUP" ]; then
       echo -n "Killing pppd: "
       killall /usr/sbin/pppd
       sleep 5
       echo
      fi

      if [ -f /var/lock/cnxadslctl ]; then
         echo -n "Stopping Conexant AccessRunner:"

         if grep -q "\[pppoatm\]" /proc/ksyms; then
            rmmod pppoatm
         fi
         killall -q cnxadslload
         rmmod CnxADSL
         rm -f /var/lock/subsys/cnxadslctl
      fi
      echo
      ;;
  status)
        cat /proc/net/atm/CnxAdsl:0 | more
        ;;
  *)
        echo "Usage: $0 {start|stop|status}"
        exit 1
esac

exit 0
----------------------------------------------------------------------------

Now configure your VPI and VCI in the 
/etc/Conexant/cnxadsl.conf

Now try to startup the ADSL connection without PPP

$invoke-rc.d cnxadslctl start

Wait 5 minutes, normaly are enoght and execute 

$invoke-rc.d cnxadslctl status
If everythig is ok you will see:
-------------------------------------------------------------------------

Conexant AccessRunner PCI ADSL Modem Adapter Status
----------------------------------

ADSL Line Connected

Line Rates:   Receive 800 kbps     Transmit 320 kbps

ADSL Modulation:G.DMT, Rate Unlimited  /  Full Rate

ATM Virtual Channel IDs: VPI: 8   VCI: 35
-------------------------------------------------------------------------------------

Now you need to configure ppp so create a file in /etc/ppp/peer with the name 
ADSLcon this is my example.
Pay attention at pppoatm parameter and user
The pppoatm param 8.35 are my VPI and VCI, set yours. 
user is the username to connect to provider.

------------------------------------------------------------------------------------
debug
plugin /usr/lib/pppd/2.4.2/pppoatm.so 8.35
mtu 1500
mru 1500
#mru 1492
#mtu 1492
noipdefault
defaultroute
usepeerdns
noauth
#ipcp-accept-remote
#ipcp-accept-local
nobsdcomp
nodeflate
nopcomp
novj
novjccomp
persist
user "piccinno.alberto"
--------------------------------------------------------------------------------

At the end you need chap-secrets
-------------------------------------------------------------------------------------
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses

'username' * 'password' *
 ------------------------------------------------------------------------------------

And now startup the connection: 
$pppd call ADSLcon


That's all. 

Alberto Piccinno.

---

### Post by fsman on 2005-01-29
Anyone got this working with Hoary?

when i $invoke-rc.d cnxadslctl start
I get errors such as 
"dowload ARM microcode failed"
"bad ioctl.."

any ideas - it works fine on woody.

---

### Post by fsman on 2005-02-02
Can anyone help me getting this working on hoary? I need to move to xorg to get cinelerra working.

---

### Post by fsman on 2005-02-02
Looks like there is a conflict between the driver and Kernel 2.6.10
Found this [http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html](http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html)

WARNING: Due to an API change in kernels 2.6.10 and 2.4.29 this device driver currently does not work in those kernels and all future kernels. This will be fixed, but not soon since I am very busy. If there are any C developers who want to have a go the fix should be very simple. A quick browse through the 2.6.10 CHANGELOG leads me to infer the following:
The pci.txt file should have information on the pci_find_device and pci_find_subsys going away and hence I guess that uses of pci_find_device should be replaced with one of:
pci_get_device, pci_dev_put, pci_dev_present, for_each_pci_dev :-(

---

### Post by tetzu0 on 2005-02-11
made a quickfix. sent it to the guy but he seems to be busy indeed the patch wasn't published yet, so here it goes...

<br>
get the sources here: http://patrick.spacesurfer.com/linu...t_pci_adsl.html<br>
get the patch here: http://tetzu0.homeip.net/code/CnxADSL-6.1.2.007-PIM-2.6-1.1.patch-2.6.10.bz2<br>

cheerz,
tetzu0

---

### Post by qualsiasinick on 2005-04-28
i'm sorry...i know that i'm little stupid...but when i try to install this driver i have a problem...
you wrote
> Build the Makefile running configure.
$ ./configure
but if i write ./configure i have an error  (bash ./configure no such file or directory)...in fact there is no file which that name,,,so what i have to do?
Ps: i'm using ubuntu 5.04

---

### Post by gnomeza on 2005-06-15
Hi

> but if i write ./configure i have an error (bash ./configure no such file or directory)...in fact there is no file which that name,,,so what i have to do?
Don't worry about it.
If you have the sources from this site [http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html](http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html) then skip the ./configure and go straight on to ```
$ make
```

> when i $invoke-rc.d cnxadslctl start
I get errors such as
"dowload ARM microcode failed"
"bad ioctl.."
OK, this is because of a conflict with Linux IOCTLs (special functions used to control device drivers). The IOCTLs in this driver use the 0x25 magic number.

The dirty solution is to edit CommonData.h replacing the line

```
#define TIGR_MAGIC '%'
``` with ```
#define TIGR_MAGIC 0xB5
```
Now this is a BAD solution. Why? Because I've randomly chosen a value (0xB5 = 181) as a new magic number. This number doesn't seem to be used by anything else (for now), but I can't guarantee this won't break things (because you have some obscure drivers loaded that clash with this).

A second problem is that recent kernels have moved the TASK_COMM_LEN definition around so I had to add it back in to the drivers.
In KernelModule/KThread.c immediately above this block:
```
/* initialize new created thread. Called by the new thread. */
extern
void init_kthread(kthread_t *kthread, char *name, int boost )
```
Add the line:
```
#define TASK_COMM_LEN 16
```

The patch which includes the two changes above is here: [http://l003026.zseriespenguins.ihost.com/~gnome/CnxADSL-6.1.2.007-PIM-2.6-1.3-Ubuntu-Hoary.patch](http://l003026.zseriespenguins.ihost.com/~gnome/CnxADSL-6.1.2.007-PIM-2.6-1.3-Ubuntu-Hoary.patch)
The drivers being patched against are here: [http://patrick.spacesurfer.com/adsl/CnxADSL-6.1.2.007-PIM-2.6-1.3.tar.bz2](http://patrick.spacesurfer.com/adsl/CnxADSL-6.1.2.007-PIM-2.6-1.3.tar.bz2)

Assuming you've followed xpic's instructions, after you extract the driver in /root, copy my patch to /root then patch the driver like so:
```

cd /root/CnxADSL-6.1.2.007-PIM-2.6-1.3
patch -p1 < /root/CnxADSL-6.1.2.007-PIM-2.6-1.3-Ubuntu-Hoary.patch

```

There. Now it should actually build and load...

Now because I'm just too lazy to recompile the kernel, before I built the driver, I also commented out the lines in KernelModule/Version.h that check if CONFIG_PREEMPT has been set in the kernel. This change is not included in the patch, but the drivers still work fine on the 2.6.10-5-386 kernel (which has CONFIG_PREEMPT enabled.)
So you don't even have to recompile the kernel!

The init script needs some tweaking for Ubuntu:

[list=1]
[*]The "common functions for init scripts" script is not where the drivers expect it.
(Although I notice xpic's script comments that line out, since the functions aren't used anyway.)
The quick solution is to add a link in the /etc/init.d directory
```
ln -s /lib/lsb/init-functions /etc/init.d/functions
```
[*] /proc/ksyms has been replaced by /proc/kallsyms in 2.6 kernels.
So replace all occurrences of ksyms with kallsyms in the init script. 

[*]The lock file should be in /var/lock/cnxadslctl
So replace all occurrences of /var/lock/subsys/cnxadslctl with /var/lock/cnxadslctl in the init script. (xpic! You missed one! ;) )
[/list] 

Phew. OK. When I get home tonight I'll add the init script changes to the patch.
I know nothing about creating packages for Ubuntu and don't have the time to learn, so someone else will have to create one.

ciao
  Mark

-- 
[http://l003026.zseriespenguins.ihost.com/~gnome/](http://l003026.zseriespenguins.ihost.com/~gnome/)

---

### Post by stefanino on 2006-01-25
someone can use this modem with ubuntu 5.10 and kernel 2.6.12 ?

---

### Post by drjoene on 2006-05-24
Hi,

I'm trying to gettings this modem run with an isdn ADSL line. Everything went fine, installing the drivers, so the modem works fine. But when i put the line into it, it won't synchronise.

Is someone familiar with this problem, and now howto solve this? Or is it not possible to get this modem work over an isdn ADSL line?

Thanks in advance,

// drJoene

---

