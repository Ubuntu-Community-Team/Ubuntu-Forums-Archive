---
title: "unable to mount external drive"
date: 2011-11-19
forum: Hardware
---

### Post by Legeril on 2011-11-19
Hey guys,

Running 10.04, I've got a 1TB external drive that until now worked perfectly. I was transferring some movies over there and it went to hell. Basically I cant mount the drive anymore, I'll post the error I get and hopefully you can help me decrypt it and offer any advice on how to fix the issue

> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

any help is greatly appreciated as I don't want to lose 700+GB of data

---

### Post by WasMeHere on 2011-11-19
Hi Legeril,

> NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important!

The NTFS file system is damaged. It suggests (and I suggest too) that you repair it using Windows. Run a dosprompt (~ terminal window) and enter the command
```
chkdsk [COLOR="Red"]E:[/COLOR] /f
```
where [COLOR="Red"]E:[/COLOR] is the name of the partition. You must check what letter it should be in Windows and change it to fit your external drive.

Good luck :-)
Olle

---

### Post by Legeril on 2011-11-19
Thanks Olle,

I understood that is wants me to 'chkdsk', but how to found the names of the variables you mentioned "E:" and "f/". The error sounds like it's for Windows, yet I am running Ubuntu.. This confuses me some

---

### Post by WasMeHere on 2011-11-19
Well, NTFS is a Windows file system, and there is no good repair tool for it in Linux due to licensing issues (it is owned by Microsoft). So people who use NTFS must be prepared to run Windows in order to repair it. Do you have Windows in any computer or can you borrow a computer for this task?

You should be able to identify the volume id (letter) for the partition using for example Microsoft Explorer (for files, not Internet Explorer).

*Edit:*
***E:*** is what you should look for and probably change.
***/f*** should not be changed, it tells chkdsk to try to repair errors (not only check for them).

---

