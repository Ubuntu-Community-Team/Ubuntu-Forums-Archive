---
title: "eucalyptus: unable to run instance"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by abhikdas27 on 2009-06-14
On ubuntu setup I have installed eucalyptus 1.5 as guided by [https://help.ubuntu.com/community/Eucalyptus](https://help.ubuntu.com/community/Eucalyptus). At step 5: creating VM image, I'm bundling vmlinuz-2.6.28-11-server instead of vmlinuz-2.6.28-11-generic. Step 5 of bundling & uploading went fine.
However, step 6 failed....
I executed....
*ec2-run-instances emi-**** --kernel eki-### --ramdisk eri-%%% -k mykey --url http://<my system ip addr>:8773/services/Eucalyptus*
I got following message....
*Server: SERVICE: FinishedVerify PROBLEM: null MSG-TYPE: RunInstancesType*
 
Any idea how can I have the image instance running? The message is described as a known bug in eucalyptus 1.4 but I'm running v1.5!

---

### Post by ramki_seeker on 2009-12-11
Hello,

I am also getting the same error. I am using Eucalyptus 1.6.

when I try to run the image, getting the following error:
*Server: SERVICE: FinishedVerify PROBLEM: null MSG-TYPE: RunInstancesType*

Have you got any solution for this? if so please help, to fix this issue.

Thank you in Advance,
Ramki

---

