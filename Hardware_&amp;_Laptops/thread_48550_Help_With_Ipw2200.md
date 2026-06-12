---
title: "Help With Ipw2200"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by jodar on 2005-07-13
When following this guide:

[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

which is great so far, I get to the step where I do:

make
sudo make install


I can't do this step as I'm getting an error saying that "is_multicast_ether_addr" is redefined.  The problem is I can't find any solution for this online anywhere....can anyone help me out?

I'm trying to get wireless internet to work on a dell inspiron 9300 and having little luck...I can't get ndiswrapper to work and thought I'd give this a try but am having this problem.

Thanks for any help.

---

### Post by luca_linux on 2005-07-13
Yes, this is a known issue. Are you running kernel 2.6.12, aren't you?
[http://bughost.org/bugzilla/show_bug.cgi?id=702](http://bughost.org/bugzilla/show_bug.cgi?id=702)
Anyway, just install the driver released yesterday, ipw2200 version 1.0.5.

---

### Post by jodar on 2005-07-13
Okay, new problem.  I tried to install the new stuff, but now it does this when I try to do the "make"

"

ERROR: ieee80211.h not found in '/lib/modules/2.6.12/include/'.

You need to install the ieee80211 subsytem from [http://ieee80211.sf.net](http://ieee80211.sf.net) and point this build to the location where you installed those sources, eg.:

%make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1

"

any misspellings are my mistyping since I'm posting from my windows box....

I have gone to the website given, and done the install routine it tells me to, but it doesn't seem to put files where this thing is looking... (I actually don't even have a /lib/modules/2.6.12/include" folder.....anyhow, I copied my ieee80211.h file over to all the locations mentioned and it doesn't do anything....arg...so frustrating.


any help?

---

### Post by leezer3 on 2005-07-14
[QUOTE=jodar]Okay, new problem.  I tried to install the new stuff, but now it does this when I try to do the "make"

"

ERROR: ieee80211.h not found in '/lib/modules/2.6.12/include/'.

You need to install the ieee80211 subsytem from [http://ieee80211.sf.net](http://ieee80211.sf.net) and point this build to the location where you installed those sources, eg.:

%make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1

"

any misspellings are my mistyping since I'm posting from my windows box....

I have gone to the website given, and done the install routine it tells me to, but it doesn't seem to put files where this thing is looking... (I actually don't even have a /lib/modules/2.6.12/include" folder.....anyhow, I copied my ieee80211.h file over to all the locations mentioned and it doesn't do anything....arg...so frustrating.


any help?[/QUOTE]
 Just a thought from me- You aren't running a 686 kernel are you?
This caused a horrible amount of problems for me, mainly as it was trying to look in & install to the 386 kernel directory. If not, you might want to talk to the folks on the #ipw2200 channel at irc.freenode.org - They fixed my IPW2100 where nobody else could (They ought to be able to; they wrote this thing :) )

-Leezer-

---

### Post by jodar on 2005-07-14
I think I am running a 686 kernel (it says 686 when i open the control center).....I may just start over from scratch, but it stinks cause the guy whose guide to setting kubuntu up on an i9300 did a great job and he set up alot of features that otherwise don't function (media control buttons on front of laptop, power features, etc.)  anyhow, I don't know if his patches will work on a different kernel (I'm new to how exactly it works and if they're easy to change for kernels, etc.)

---

### Post by luca_linux on 2005-07-18
Since the latest driver (1.0.5 and then 1.0.6) ieee80211 is not built in anymore.
Anyway, I'll update my HowTo soon, probably by tomorrow.

---

### Post by leech on 2005-07-27
Not sure if someone fixed this problem yet or not, but the solution I found was pretty much what it tells you.  Download the ieee80211 from sourceforge.net and do a make and make install on it, THEN install the ipw2200.  Ran into this problem on my laptop after trying to make a 2.6.12.3 kernel (which is running fine now.)  Though I built this with standard Debian, it should work the same on Ubuntu.

Leech

---

### Post by luca_linux on 2005-07-27
Yes, I explained it in my updated HowTo: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by RickKnight on 2006-01-07
Hi. Hope someone is still watching this thread.

I had ipw2200 working Kubuntu 5.0.4 but aftre upgrading to Kubuntu 5.10, ipw2200 has stopped working. I've removed the prior installation and the ipw2100-source that comes with Kububtu. I've followed luca_linux's howto but 'make ipw2200' failes with this output...

```
mkdir -p /home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions
cp /lib/modules/2.6.12-10-386/net/ieee80211/.tmp_versions/*.mod /home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions
make -C /lib/modules/2.6.12-10-386/build M=/home/share/ipw2200/ipw2200-1.0.9 MODVERDIR=/home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/share/ipw2200/ipw2200-1.0.9/ipw2200.o
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c: In function `ipw_wpa_set_encryption':
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:6679: warning: passing arg 1 of pointer to function makes pointer from integer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:6679: error: too few arguments to function
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c: In function `ipw_send_qos_params_command':
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:7590: warning: passing arg 3 of `ipw_send_cmd_pdu' makes integer from pointer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:7590: warning: passing arg 4 of `ipw_send_cmd_pdu' makes pointer from integer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c: In function `ipw_send_qos_info_command':
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:7597: warning: passing arg 3 of `ipw_send_cmd_pdu' makes integer from pointer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:7597: warning: passing arg 4 of `ipw_send_cmd_pdu' makes pointer from integer without a cast
make[2]: *** [/home/share/ipw2200/ipw2200-1.0.9/ipw2200.o] Error 1
make[1]: *** [_module_/home/share/ipw2200/ipw2200-1.0.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
root@w43wxp121:/home/share/ipw2200/ipw2200-1.0.9 #          
``` 

I'm stuck here. Can anyone help me get around this?

Thanks
Rick Knight

---

### Post by xMetaRidley on 2006-01-08
[QUOTE=RickKnight]Hi. Hope someone is still watching this thread.

I had ipw2200 working Kubuntu 5.0.4 but aftre upgrading to Kubuntu 5.10, ipw2200 has stopped working. I've removed the prior installation and the ipw2100-source that comes with Kububtu. I've followed luca_linux's howto but 'make ipw2200' failes with this output...

```
mkdir -p /home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions
cp /lib/modules/2.6.12-10-386/net/ieee80211/.tmp_versions/*.mod /home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions
make -C /lib/modules/2.6.12-10-386/build M=/home/share/ipw2200/ipw2200-1.0.9 MODVERDIR=/home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/share/ipw2200/ipw2200-1.0.9/ipw2200.o
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c: In function `ipw_wpa_set_encryption':
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:6679: warning: passing arg 1 of pointer to function makes pointer from integer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:6679: error: too few arguments to function
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c: In function `ipw_send_qos_params_command':
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:7590: warning: passing arg 3 of `ipw_send_cmd_pdu' makes integer from pointer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:7590: warning: passing arg 4 of `ipw_send_cmd_pdu' makes pointer from integer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c: In function `ipw_send_qos_info_command':
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:7597: warning: passing arg 3 of `ipw_send_cmd_pdu' makes integer from pointer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:7597: warning: passing arg 4 of `ipw_send_cmd_pdu' makes pointer from integer without a cast
make[2]: *** [/home/share/ipw2200/ipw2200-1.0.9/ipw2200.o] Error 1
make[1]: *** [_module_/home/share/ipw2200/ipw2200-1.0.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
root@w43wxp121:/home/share/ipw2200/ipw2200-1.0.9 #          
``` 

I'm stuck here. Can anyone help me get around this?

Thanks
Rick Knight[/QUOTE]

Try applying [this]("http://ipw2200.sourceforge.net/patches/ipw2200-1.0.9-qos_param_fix.patch") patch with the command 

patch -p0 < ipw2200-1.0.9-qos_param_fix.patch

then try to compile again. You must place this patch in the directory above the ipw2200-1.0.9 directory.

---

### Post by RickKnight on 2006-01-08
[QUOTE=xMetaRidley]Try applying [this]("http://ipw2200.sourceforge.net/patches/ipw2200-1.0.9-qos_param_fix.patch") patch with the command 

patch -p0 < ipw2200-1.0.9-qos_param_fix.patch

then try to compile again. You must place this patch in the directory above the ipw2200-1.0.9 directory.[/QUOTE]
Thanks for your reply. I applied the patch and it seems to get me further along in the build, but I'm still getting an error...
```
mkdir -p /home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions
cp /lib/modules/2.6.12-10-386/net/ieee80211/.tmp_versions/*.mod /home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions
make -C /lib/modules/2.6.12-10-386/build M=/home/share/ipw2200/ipw2200-1.0.9 MODVERDIR=/home/share/ipw2200/ipw2200-1.0.9/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/share/ipw2200/ipw2200-1.0.9/ipw2200.o
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c: In function `ipw_wpa_set_encryption':
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:6679: warning: passing arg 1 of pointer to function makes pointer from integer without a cast
/home/share/ipw2200/ipw2200-1.0.9/ipw2200.c:6679: error: too few arguments to function
make[2]: *** [/home/share/ipw2200/ipw2200-1.0.9/ipw2200.o] Error 1
make[1]: *** [_module_/home/share/ipw2200/ipw2200-1.0.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2

```
Any other suggestions? 

Thanks again,
Rick Knight

---

