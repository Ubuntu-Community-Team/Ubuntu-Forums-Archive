---
title: "Restoring my system on a different laptop"
date: 2008-07-16
forum: General Help
---

### Post by Radioman991 on 2008-07-16
Hello:

Here is my situation

1)  Company laptop runs windows...but after done with Windows, I boot to Hardy from an external USB drive.  Been working great for several months.  Laptop is a Thinkpad T43p

2)  OLD company laptop, a Dell D610, the wife is using for school, but will soon relinquish back to me.

I would like to restore the current Hardy system I am running on the USB drive to the Dell laptop.  Why not just do a new install?  Well, I have XP running under VMware on the system with the external USB, and I would NOT like to lose the database, and licensing on the 2 software packages I am running on that VM.  If someone can tell me how to get that VM OUT of the USB drive, and restored onto the Dell laptop, now THEN I could do a fresh install on the other machine.

Thanks as always :-)

Radioman

---

### Post by danwood76 on 2008-07-16
If you set the partitioning the same as on your USB disk then theres probably not a lot short of just using the tar method to backup the USB disk and restore it to your D610.
You could even just do a CP across but you may mess up the permissions.
Have a quick look on the forums for the tar backup method.

You will need to update all the UUID's and block IDs in your fstab and menu.lst to suit the laptop but once thats done it should just work.

---

### Post by Radioman991 on 2008-07-16
That thought occoured to me, but the Dell has a 60 gig drive, the USB is 100 gig.

If I knew how to just backup the 20 gig XP "partition" VMWare put on the drive, I'd be happy.

---

### Post by jimv on 2008-07-16
HMMM.  VMware virtual machines's are stored in files, so couldn't you just copy the files for the XP VM to the Dell Laptop once you install Ubuntu and VMware on it?  What I'm saying is that VM's are portable....they aren't tied to a specific VMware installation.

EDIT

I just looked on my XP box that has VMware installed, and VMware creates a folder for each virtual machine that contains all the files you need to run that virtual machine.  So you can just copy the folder for your XP VM to the Dell machine and it should work just fine.

---

