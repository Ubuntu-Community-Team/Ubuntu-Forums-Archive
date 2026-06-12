---
title: "[SOLVED] Help installing flash player 9 on Ubuntu 8.04"
date: 2008-10-13
forum: General Help
---

### Post by fs_tigre on 2008-10-13
Hi,

I’m completely new to linux (Ubuntu).  I installed Ubuntu on my pc and I’m surprised how fast it runs in comparison with windows vista, I’m very happy with the performance but at the same time I’m a little frustrated with something that should be pretty simple.

I have been trying to install flash player 9 on Ubuntu 8.04 but for some reason I cannot make this work.  Could someone be so kind and walk me through step by step (if possible) on how to do this? Remember I’m new to Ubuntu (Linux), so please go easy on me. 
Thanks,
fs_tigre

---

### Post by snowpine on 2008-10-13
Open a terminal (Applications -> Accessories) and type:

```
sudo apt-get install flashplugin-nonfree
```

Enter your password when prompted.

---

### Post by fs_tigre on 2008-10-13
Wow, I just posted this probably five minutes ago and I already have a reply thanks.

Do I need to download flash player first? Or just by typing this will do the trick?

Sorry, I'm not using this computer right now to give it a try.

Thanks,
fs_tigre

---

### Post by snowpine on 2008-10-13
The instructions I gave you are the easy ones; no need to do anything else. :)

Here's a little lesson on how ubuntu works. Feel free to tune me out if you like. :) There are two main ways you can install software in Ubuntu: 1) by downloading packages (.deb or .tar.gz for example); 2) from the repositories (using apt-get, synaptic, or add/remove programs).

Most people coming to Ubuntu from Windows are used to finding a software online, downloading it, and running the .exe installer. This is equivalent to the first method (download the .tar.gz and double-click to install it), and it works for Flash if you download it from the Adobe website. However, it is recommended to use the second method (from the repositories) whenever possible. The repositories consist of applications and other packages that are tested to work with your ubuntu install and can be considered "safe and trusted."

sudo apt-get install flashplugin-nonfree
sudo = execute the following command with Super User privilages
apt-get = access the Ubuntu repositories
install = install the following package
flashplugin-nonfree = name of the package to install (nonfree because it's proprietary Adobe sofware, which is why it can't be pre-installed in Ubuntu)

---

### Post by fs_tigre on 2008-10-13
You are my Hero snowpine, you read my mind. Awesome explanation I needed this.

Thank you very much.

---

### Post by houbysoft.xf.cz on 2008-10-13
Nice explanation. I just thought that you deserve thanks so I thanked you (even if I knew the things you posted :D)

---

