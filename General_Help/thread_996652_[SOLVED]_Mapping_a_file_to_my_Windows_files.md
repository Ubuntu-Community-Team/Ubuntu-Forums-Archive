---
title: "[SOLVED] Mapping a file to my Windows files"
date: 2008-11-29
forum: General Help
---

### Post by DouglasT on 2008-11-29
Hello! I'm very new to Ubuntu (this is actually my first day) and I need some help. 

First I should probably mention that right now I'm dual booting Ubuntu and Windows XP Home. To install Ubuntu, I loaded the live disc and selected the "Install Inside Windows" option. So, I don't have a separate partition for Ubuntu, Windows and Unbuntu share a partition.

My goal right now is to be able to access the files that I have on Windows from Ubuntu. I did accomplish this with a Google search and these commands:

    * cd /mnt
    * sudo mkdir windrive 
    * sudo mount -t ntfs /dev/sda1 /mnt/windrive -o “umask=022&#8243;
    * ls windrive

Which worked fine. But, after a reboot, the files that I created(/gained access to) in doing that where no longer there(/accessible)

I can go Places > Computer > File System > mnt > windrive, but the windrive folder is empty. 

So, I need to know how to map a folder to my Windows folders permanently, and, if partitioning is required to do so, I need to know how to create a separate partition for Ubuntu.

Thanks in advance!

-Doug

---

### Post by vanadium on 2008-11-29
To permanently mount your Windows partition, you should include a line into your /etc/fstab. This will make sure the mounting, which you are now doing with the "mount" command", is done during startup. There is plenty of documentation to be found on the web ("ubuntu mount ntfs /etc/fstab")

For convenient and safe access to your user files on your Windows partition, you should create a link to your "My documents" folder in Windows in your Ubuntu home. That way, you will have convenient access to your actual files from within your home. There will be no need to navigate outsied of your home directory to /mnt/windrive to access your files. Additionally, you will get directly to your user files. There will be no need to first navigate though Windows system directories. In addition to convenience, you have added safety. You can create links using the nautilus file manager: Press Ctrl+Sft and drag the windows "My Documents" folder to your home directory. With the command line, it will look like (not exactly, but to give you the idea):

ln -s "/mnt/windrive/Documents And Settings/Users/.../My Documents" "~/My Documents"

---

