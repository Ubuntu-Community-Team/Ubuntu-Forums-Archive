---
title: "pm-hibernate causes entering grub boot menu on wake"
date: 2012-03-21
forum: Hardware
---

### Post by monochromec on 2012-03-21
Strange behaviour on oneiric (tried it with 3.0 and 3.1 kernels):

Sometimes pm-hibernate causes the PC  to enter grub upon wake (either power button or wake on LAN) while GRUB_TIMEOUT and GRUB_HIDDEN_TIMEOUT still remain 0 in the Grub 2 configruation file and no key was pressed on the keyboard during boot.  

Even stranger: this behaviour is NOT reproducible but happens more or less randomly. 

Information in pm-logs  is inconclusive.

Any thoughts?

---

### Post by monochromec on 2012-04-12
Finally found a work-around to this problem. Apparently the problem is that pm-hibernate does not always unset the grub environment variable "recordfail" correctly (or the modification doesn't make it into the grub environment block - see /etc/pm/sleep.d/10_grub-common). Hence, upon checking this variable at boot time grub disregards the timeout and displays the normal boot menu. 

A possible work-around for this problem is now to modify the header section of the grub stanza (file /etc/grub.d/00_header) so that around line 234 (in my Oneiric instance) 

```
make_timeout ()
{
    cat << EOF                                                                                                                                                                   
if [ "\${recordfail}" = 1 ]; then                                                                                                                                              
   set timeout=-1                                                                                                                                                               
else                                                                                                                                                                           
   set timeout=${2}                                                                                                                                                              
 fi                                                                                                                                                                             
EOF                                                                                                                                                                              
}

```
becomes 

```

make_timeout ()
{
    cat << EOF                                                                                                                                                                   
# if [ "\${recordfail}" = 1 ]; then                                                                                                                                              
#   set timeout=-1                                                                                                                                                               
# else                                                                                                                                                                           
   set timeout=${2}                                                                                                                                                              
# fi                                                                                                                                                                             
EOF                                                                                                                                                                              
}

```

I'm filing this also as a launchpad bug.

---

### Post by aparigraha on 2012-05-28
Thanks for your effort in noting and bugging this.

The proposed workaround does NOT work for me however.


ASUS U31J
Ubuntu 12.04 64

---

