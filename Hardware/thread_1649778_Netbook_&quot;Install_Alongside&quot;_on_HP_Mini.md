---
title: "Netbook &quot;Install Alongside&quot; on HP Mini?"
date: 2010-12-20
forum: Hardware
---

### Post by Chernevik on 2010-12-20
I want install Ubuntu Netbook 10.10 on an HP Mini, dual boot with Windows Starter Whatever.  Alas, the 'install alongside' option doesn't appear; my only options are 'use the whole drive' or edit the partition table manually.  None of the partitions proposed look right for the Windows data, except possibly for the one whose usage is 'unknown'.

Any suggestions for how I can get Ubuntu to provide the 'install alongside' option?  Or how I can go about manually editing the partitions without blowing up Windows?

---

### Post by Quackers on 2010-12-20
If you're using the 10.10 installer you really don't want the "install alongside" option! It has major problems at the moment (ie over-writing your system).
First thing to check is to go in to the Windows disk management screen and check how many primary partitions already exist. If you have 4 you will need to delete one before you do anything else.
If you have 3 or less primary partitions you will almost certainly need to shrink one of them to give some free space for Ubuntu to install into.

---

