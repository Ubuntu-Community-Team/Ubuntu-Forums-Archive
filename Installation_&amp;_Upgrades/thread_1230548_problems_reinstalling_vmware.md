---
title: "problems reinstalling vmware"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by mendocinosunrise on 2009-08-03
Help! I had vmware up & running beautifully until I monkeyed around & installed zoneminder. Being the world's biggest ubuntu rookie, I'm sure I mucked up the works somehow.
Vmware wouldn't open, so I tried re-running vmware-config.pl. 
Got the message:
[COLOR=DarkGreen]Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.3.3". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.3.3" anyway? [no][/COLOR]
[COLOR=Black]
After googling that error, I found a patch at [https://help.ubuntu.com/community/VMware/Server ]("https://help.ubuntu.com/community/VMware/Server")and followed the instructions to install the patch. Still got the above error when trying to run vmware-config.pl. 
SooOOooo... I uninstalled vmware & tried reinstalling. Same error. Here's the rest of the terminal output:
[COLOR=Green]Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.3.3". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.3.3" anyway? [no] yes

What is the location of the directory of C header files that match your running
kernel? 
[/lib/modules/2.6.30-020630rc3-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.30-020630rc3-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630rc3-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:31:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:67: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630rc3-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.[/COLOR]


any help would be greatly appreciated!
[/COLOR]

---

### Post by digital_sabine on 2009-11-04
I'm getting something nearly identical to this after upgrading from 9.04 to 9.10.  Mind you, it was not a smooth upgrade (mouse/keyboard froze, screen went mostly dark, and I could never click 'yes' to the question asking me if I wanted to discard unused packages), so I'm very aware that this may be a botched upgrade, and I may have to wipe and install 9.10 fresh.

However... if I don't have to nuke 'n' pave, I don't want to. ;) Any advice would be appreciated.

sandra

---

### Post by mortenr on 2009-11-05
I got almost the same errors on a fresh 9.10 install - first error message the same, the details a bit different. This seemed to work:

[http://mariuszczyz.wordpress.com/2009/06/10/kernel-2-6-29-and-vmware-2-vmware-config-pl-problems/](http://mariuszczyz.wordpress.com/2009/06/10/kernel-2-6-29-and-vmware-2-vmware-config-pl-problems/)

VMWare server 2 is now configuring itself nicely.

Hope this helps.

Regards,
Morten

---

### Post by mortenr on 2009-11-05
Arg. Undo. No can do - vmnet still refuses to compile. Bugrit...

Error message:

/tmp/vmware-config3/vmnet-only/netif.c: In function &#8216;VNetNetIfSetup&#8217;:
/tmp/vmware-config3/vmnet-only/netif.c:201: error: &#8216;struct net_device&#8217; has no member named &#8216;init&#8217;
/tmp/vmware-config3/vmnet-only/netif.c:202: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/tmp/vmware-config3/vmnet-only/netif.c:203: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/tmp/vmware-config3/vmnet-only/netif.c:204: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/tmp/vmware-config3/vmnet-only/netif.c:205: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/tmp/vmware-config3/vmnet-only/netif.c:206: error: &#8216;struct net_device&#8217; has no member named &#8216;set_mac_address&#8217;
/tmp/vmware-config3/vmnet-only/netif.c:207: error: &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
make[2]: *** [/tmp/vmware-config3/vmnet-only/netif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmnet-only'
Unable to build the vmnet module.

---

### Post by mortenr on 2009-11-05
Aha! I removed the binary directory under vmware/modules, used the tars from here

[http://www.jwh.me.uk/](http://www.jwh.me.uk/)

and bingo! vmnet compiles and VMWare Server 2 starts just fine.

---

### Post by digital_sabine on 2009-11-05
I wanted to follow up: I did end up doing a reinstall of 9.10, but I still could not install VMWare with the same messages.  Then I found this post, and the script provided worked like a charm.

[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

A huge shout out of 'Thanks' to Radu.  I would have been dead in the water without his script!

sandra

---

