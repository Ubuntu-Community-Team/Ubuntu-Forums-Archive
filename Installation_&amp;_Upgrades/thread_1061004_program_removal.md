---
title: "program removal?????"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by jblinuser on 2009-02-05
i have recently installed vmware player and server. i started using vmware server and installed a vm of windows vista and another one of windows xp. i was going to use them if i ever needed a windows machine but i have another computer that i can use for that. i have been having some issues with the server and player since i installed them and i would like to remove them from my machine. i had to install them using the cli and i dont know how to remove them using the cli. can some one help me with this please?

---

### Post by taurus on 2009-02-05
Do you remember how you installed them from a terminal, commands?

---

### Post by jblinuser on 2009-02-05
here is the link to the site that i copied and pasted from

[http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/](http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/)

---

### Post by taurus on 2009-02-05
Do you remember where you unpacked the VMware-server-1.0.8-126538.tar.gz because there should be a vmware-uninstall.pl script in there?

---

### Post by jblinuser on 2009-02-05
all of the files were unpacked in my home folder. only one that i see that even comes close is an install.sh file. i dont even see the intall.pl file.

---

### Post by jblinuser on 2009-02-05
i am unable to find any way to uninstall this software. can anyone help?

---

### Post by overlord.gaurav on 2009-02-05
Try running 'sudo vmware-uninstall.pl'

---

### Post by jblinuser on 2009-02-05
it says command not found when i do that.

---

### Post by taurus on 2009-02-05
Where in your $HOME did you unpack it?  Can you _change_ (cd) to that directory and post the output of this command?

```
ls -la
```

---

### Post by mashiox on 2009-02-05
I think what they're trying to get across is they want you to, in a terminal, change your directory to the folder where you extracted the vmware tarball (file ending with tar.gz, .tar, etc.)

So, if you extracted vmware on the Desktop to a folder named vmware it will be in /home/your-user-name/Desktop/vmware

To do this in a terminal: 

cd /home/your-user-name-here/Desktop/vmware-folder-name-here

Then, there should be a uninstall perl script on that folder.
You can check by typing ls in the terminal and looking for vmware-uninstall.pl

If you find it type this in the terminal

sudo ./vmware-uninstall.pl

If you can't find it, try this command in the terminal
find / -name vmware-uninstall.pl

I'd bet your likely using Ubuntu though, so you can also try 
sudo apt-get remove vmware

---

### Post by jblinuser on 2009-02-05
ok i found that file and performed the uninstall. i was just looking in the home directory rather than taking it a step further and actually going into the vmware folder to find the uninstall file. thanks for the help everyone.

---

