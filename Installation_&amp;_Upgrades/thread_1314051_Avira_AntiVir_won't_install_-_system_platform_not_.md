---
title: "Avira AntiVir won't install - system platform not supported"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by xq2003 on 2009-11-04
Hi everybody,

today, I tried to install AntiVir on my Ubuntu 9.10 (Kernel 2.6.31-14). As I ran the install script, the message "It is not possible to install AVIRA AntiVir Workstation (UNIX), because your system platform is not supported." I then did some research but it strangely seems that I'm the only one experiencing this problem. Is there anybody out there who has managed to install AntiVir on Karmic? Any help would be greatly appreciated :D

PS: If you wonder why I hold it necessary to install antivirus software on Ubuntu: I'm planning to install it to my Live USB to scan a friend's windows PC ;)

---

### Post by yus253 on 2009-11-04
> **xq2003 said:**
> Hi everybody,

today, I tried to install AntiVir on my Ubuntu 9.10 (Kernel 2.6.31-14). As I ran the install script, the message "It is not possible to install AVIRA AntiVir Workstation (UNIX), because your system platform is not supported." I then did some research but it strangely seems that I'm the only one experiencing this problem. Is there anybody out there who has managed to install AntiVir on Karmic? Any Help would be greatly appreciated :D

PS: If you wonder why I hold it necessary to install antivirus software on Ubuntu: I'm planning to install it to my Live USB to scan a friend's windows PC ;)

When I opened the folden of ../ariva/antivir-workstation-pers-3.0.5-11/contrib /dazuko
I was finding a file that named  supported_distros.Reading  it ,I  know what system it will be supported,but it not includ Karmic koala.so……we just waiting avira supported.:lolflag:
&#32456;&#20110;&#26126;&#30333;&#20026;&#20160;&#20040;avira for linux&#19981;&#33021;&#23433;&#35013;&#20102;&#12290;&#25171;&#24320;&#20320;&#19979;&#36733;&#30340;../ariva/antivir-workstation-pers-3.0.5-11/contrib /dazuko&#65292;&#20320;&#21487;&#20197;&#25214;&#21040;&#36825;&#20010;&#25991;&#20214; supported_distros&#20013;&#25991;&#32763;&#35793;&#36807;&#26469;&#21483;&#20570;&#25903;&#25345;&#29256;&#26412;&#65306;
dazukofs-3.0.0-rc4_2.6.16_SLES10SP1:
	SLES10 SP 1 with kernel 2.6.16
	vanilla kernel 2.6.16

dazukofs-3.0.0-rc4_2.6.16_SLES10SP2:
	SLES10 SP2 with kernel 2.6.16

dazukofs-3.0.0-rc4_2.6.18:
	Debian 4 (etch)
	vanilla kernel 2.6.18

dazukofs-3.0.0-rc4_2.6.20:
	Redhat 5.x with kernel 2.6.18.x
	vanilla kernel 2.6.20

dazukofs-3.0.0-rc4_2.6.22:
	vanilla kernel 2.6.22

dazukofs-3.0.0-rc4_2.6.22_Ubuntu7.10:
	Ubuntu 7.10 with kernel 2.6.22

dazukofs-3.0.0-rc4_2.6.24:
	vanilla kernel 2.6.24

dazukofs-3.0.0-rc4_2.6.25:
	vanilla kernel 2.6.25

dazukofs-3.0.0-rc4_2.6.26:
	Debian 5 (lenny) 
	vanilla kernel 2.6.26

dazukofs-3.0.0-rc4_2.6.27:
	vanilla kernel 2.6.27

dazukofs-3.0.0-rc4_2.6.27_ub_os11.1:
	Ubuntu 8.10
	OpenSuse 11.1
	Ubuntu 9.04
	SLES11 with kernel 2.6.27.19

---

### Post by yus253 on 2009-11-04
> **xq2003 said:**
> Hi everybody,

today, I tried to install AntiVir on my Ubuntu 9.10 (Kernel 2.6.31-14). As I ran the install script, the message "It is not possible to install AVIRA AntiVir Workstation (UNIX), because your system platform is not supported." I then did some research but it strangely seems that I'm the only one experiencing this problem. Is there anybody out there who has managed to install AntiVir on Karmic? Any Help would be greatly appreciated :D

PS: If you wonder why I hold it necessary to install antivirus software on Ubuntu: I'm planning to install it to my Live USB to scan a friend's windows PC ;)

You know Karmic koala had linux kernel 2.6.31,but dazukofs in avira don't supposed it .I also find dazukofs3.1.1 can supposed this kernel ,I have no way install it.

---

### Post by butibum on 2009-11-05
Quick and dirty workaround, worked for me, ymmmv!

Go to the script folder under where you expanded the antivir program.

The problem arises because the getsysteminfo script returns linuxglibc20 as the version of libc installed in Karmic. Actually the version is not 2.1 but 2.10, but the grep test does not know that.
I just modified the script as below:

do_classification()
{                  
        CLASS="unknown"

 case "${OS}" in
 linux) 
 CLASS=""

 if [ -f "/lib/libc.so.6" ]
 then                      
 grep "C Library.*version 2.0" /lib/libc.so.6 > /dev/null
                                RET=$?                                                  

if [ $RET -ne 0 ]
then             
grep "C Library.*version 2.1" /lib/libc.so.6 > /dev/null
# comment out the next line
#RET=$?                                                 
# add in a dummy exit code  
                                     RET=2                                                   
fi                        

Now try the install again.
hth
Badwolf9

---

### Post by kixome on 2009-11-05
use clam

---

### Post by running_rabbit07 on 2009-11-05
Bitdefender is free for home users.

---

### Post by sliketymo on 2009-11-05
I think there is an AVG,but I'm not sure about the support for 9.1.Don't bother with the stuff myself.

---

### Post by xq2003 on 2009-11-05
> **butibum said:**
> Quick and dirty workaround, worked for me, ymmmv!

Go to the script folder under where you expanded the antivir program.

The problem arises because the getsysteminfo script returns linuxglibc20 as the version of libc installed in Karmic. Actually the version is not 2.1 but 2.10, but the grep test does not know that.
I just modified the script as below:

do_classification()
{                  
        CLASS="unknown"

 case "${OS}" in
 linux) 
 CLASS=""

 if [ -f "/lib/libc.so.6" ]
 then                      
 grep "C Library.*version 2.0" /lib/libc.so.6 > /dev/null
                                RET=$?                                                  

if [ $RET -ne 0 ]
then             
grep "C Library.*version 2.1" /lib/libc.so.6 > /dev/null
# comment out the next line
#RET=$?                                                 
# add in a dummy exit code  
                                     RET=2                                                   
fi                        

Now try the install again.
hth
Badwolf9

It worked, thanks a lot! I wonder how long it will take for Avira to fix it though :p

---

### Post by running_rabbit07 on 2009-11-05
> **sliketymo said:**
> I think there is an AVG,but I'm not sure about the support for 9.1.Don't bother with the stuff myself.

I never realized Ubuntu had a January release.

---

### Post by gas85 on 2009-11-11
edit

---

