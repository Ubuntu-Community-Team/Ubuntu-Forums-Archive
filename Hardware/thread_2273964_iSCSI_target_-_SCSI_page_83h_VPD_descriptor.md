---
title: "iSCSI target - SCSI page 83h VPD descriptor"
date: 2015-04-16
forum: Hardware
---

### Post by Nathan_Hawkins on 2015-04-16
I'm trying to cluster 2 windows 2012 r2 servers using iSCSI setup on a linux server (Ubuntu 14.04 server 
with all of the appropriate packages installed to deliver iSCSI as a target - used this as a guide [http://linhost.info/2012/05/configure-ubuntu-to-serve-as-an-iscsi-target/](http://linhost.info/2012/05/configure-ubuntu-to-serve-as-an-iscsi-target/)). Both of the Windows 
servers attach to the iSCSI "drive" beautifully, but when trying to create the cluster the creation 
fails with the error "Physical disk {2ed5a1cd-5f82-463b-95b7-a08f3151a168} does not have the inquiry data 
(SCSI page 83h VPD descriptor) that is required by failover clustering." After looking into this error the 
issue is that the discovery through the iSCSI setup from the linux server does not give back a VPD Page 
83h Identifier. At first glance this appears to be corrected by 
[https://support.microsoft.com/en-us/kb/2531907](https://support.microsoft.com/en-us/kb/2531907) but it does not as all that hotfix does is correct a bug in 
which the descriptor is sent second or some other position rather than first. Windows 2012 R2 has fixed 
that bug. The issue is described better here: [http://iscsi-enterprise-target.996254.n3.nabble.com/scsi-id-scsi-sn-and-vpd-83-type-8h-td11560.html](http://iscsi-enterprise-target.996254.n3.nabble.com/scsi-id-scsi-sn-and-vpd-83-type-8h-td11560.html). So after further research it looks like scsi_id is the command I need to issue to set the 0x83 (or 83h descriptor) string, where the man pages I find are [http://manpages.ubuntu.com/manpages/dapper/man8/scsi_id.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/scsi_id.8.html) and/or [http://manpages.ubuntu.com/manpages/hardy/man8/scsi_id.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/scsi_id.8.html) but the issue Im having is that scsi_id doesnt work... I get "scsi_id: command not found" whenever I try the command. So, if anyone could help Id be very apprecaitive.


Thanks!

---

### Post by Nathan_Hawkins on 2015-04-17
So, I figured out that in order to use scsi_id you have to include the path... [FONT=Open Sans, sans-serif]/lib/udev/scsi_id --page=0x83 --device=/dev/sda2, but when I get the command to execute it doesnt return the hash for the 83h page descriptor which to me indicates its still not set right. So, sda2 is the ext3 partition I have set up to hold my iSCSI target files, but sda and sda2 are neither scsi and thus wont work with the scsi_id command. The file I have set as the target is setup as such:

[/FONT]dd if=/dev/sda2 of=/iscsi/file.img count=0 obs=1 seek=50G (sda2 is mounted to /iscsi)

and then in /etc/iet/ietd.conf I have set:

Target iqn.2015-04.domain.com:storage.sys0
Lun 0 Path=/iscsi/file.img,Type=fileio,ScsiId=lun0,ScsiSN=lun0

Still need help! Thanks!

---

