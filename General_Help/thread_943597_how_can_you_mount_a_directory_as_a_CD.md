---
title: "how can you mount a directory as a CD?"
date: 2008-10-10
forum: General Help
---

### Post by uschxc on 2008-10-10
I have a windows install directory that i need to mount as a cd for VMWare to pick it up as install media, and i just don't want to waste a disc for this.  i just don't know how to make mount do what i want

---

### Post by ubunny on 2008-10-10
maybe you could just do a symbolic link to the directory?  man ln

otherwise if it's an .iso file and you don't want to burn it, you can use mount with the "-o loop" option on the end, and it will allow you to mount the image as a regular mount directory.

---

### Post by Sycron on 2008-10-10
> **uschxc said:**
> I have a windows install directory that i need to mount as a cd for VMWare to pick it up as install media, and i just don't want to waste a disc for this.  i just don't know how to make mount do what i want

It's a iso ? If is just a directory it can't be bootable.

If it is a iso the you sure have an option in vmware to mount a iso. VirtualBox has it.

---

### Post by uschxc on 2008-10-10
its not an .iso.  its just the cd contents in a directory.  vbox has the option to mount a directory as an iso for installing an OS but vmware does not.  so i either need to make the directory an ISO and then mount the ISO but that would waste disc space with a 3.5gig image and 3.5gig folder so i was trying to see if i could mount the directory as a device so VMware would read it...not sure it needs to actually be bootable since its just going through VMware.

---

### Post by cariboo on 2008-10-10
If you have a windows install disk you can create an iso using dd. In a terminal type:

```
sudo dd if=/dev/scd0 of=windows.iso
```

You can then use your iso to install windows in a virtual machine.

Jim

---

### Post by Sycron on 2008-10-10
If you copied JUST the files on the CD, the CD is not bootable anymore.

You have to do what cariboo907 told you.

---

### Post by uschxc on 2008-10-10
not to be an *** but if i had the CD then i wouldn't need its contents in a directory mounted as a cd would i?  The directory is on a local share that is public on the network.  the disc's contents are in a folder so you don't need the windows cd everytime you change hardware or install a driver.  in this instance i need to setup a virtual windows machine, vmware is the route i'm going since vbox can boot its images, and i need the directory mounted as a device so vmware can read it.

or turn the directory into a .iso image but i would rather not waste the space

again the image vmware reads doesn't need to actually be bootable vmware just needs the cd's files for installation.

---

### Post by koenn on 2008-10-10
> **cariboo907 said:**
> If you have a windows install disk you can create an iso using dd. In a terminal type:

```
sudo dd if=/dev/scd0 of=windows.iso
```

You can then use your iso to install windows in a virtual machine.

Jim

if he has an install disk he could just let the VM attach to the physical drive and run it directly, no ?

you can create a an iso image out of a directory with mkisofs, but it won't be bootable unless you manage to insert a boot sector in it, which is not impossible ([http://support.microsoft.com/kb/167685](http://support.microsoft.com/kb/167685) ), but i doubt it's going to be easy.

---

### Post by koenn on 2008-10-10
> **uschxc said:**
> the disc's contents are in a folder so you don't need the windows cd everytime you change hardware or install a driver.  in this instance i need to setup a virtual windows machine, vmware is the route i'm going since vbox can boot its images, and i need the directory mounted as a device so vmware can read it.

or turn the directory into a .iso image but i would rather not waste the space

again the image vmware reads doesn't need to actually be bootable vmware just needs the cd's files for installation.

you can't mount a folder contents on as a device (like, mount it on /dev/cdrom ) because they're block devices, not directories. 

you can create an iso out of a directory and present that to vm as a cd
you do something like
```
 mkisofs -o winxp.iso -r -l -J  /path/to/WinXP/files
```


but, again, it won't be  bootable CD and i pretty much doubt you can set up a virtual machine if you can't boot the OS installer for it.

---

### Post by uschxc on 2008-10-10
like i said, i don't think the CD needs to be bootable.  the VM install wizard is acting as the boot and is ready for some media to install too.  i don't think its going to try and double check that the install media is bootable (since, ya know, it doesn't have to boot anything).  

i'll try the mkisofs approach i was just hoping i could make the kernel read the directory as a virtual physical device

thanks peeps

---

### Post by koenn on 2008-10-10
> **uschxc said:**
> like i said, i don't think the CD needs to be bootable.  the VM install wizard is acting as the boot and is ready for some media to install too.  i don't think its going to try and double check that the install media is bootable (since, ya know, it doesn't have to boot anything).  

install ***to*** ? you mean install from, right, or are we talking about completely different issues here ?

If by VM install wizard you mean the thingy that creates the virtual hardware (like how many CPU's you want and how big a hard drive ?) - it will create a virtual machine, that, when powered on, **will attempt to boot **, either from its hard disk, which is newly created and thus empty, or from a CD. To boot from a CD, the CD needs to be bootable.
Unless VM has advanced so much over the past few months that it can skip the boot sector and still figure out which executable to run in order to install the operating system. 

Good luck.

---

### Post by uschxc on 2008-10-10
i could see this being the case of VM didn't ask you to specify what type of OS you are about to install.  it would need boot information to figure out how to install the OS, but since you select "windows XP" or whatever i'm pretty sure it knows what to do from there and just needs the actual 
media. 

guess i'll let you know when i get a chance to try it out

---

### Post by koenn on 2008-10-10
I assume it uses your choice of OS to set some defaults that go well with the chosen OS, such as minimal required RAM or some BIOS settings or so. 

I'd be interested to know how it goes ...

---

