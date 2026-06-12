---
title: "Need help installing file."
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2009-02-06
Newbe here.
I've extracted a .tar.bz2 file & it's on my desktop. Is there a *best way* to install it?
I've search hard & cannot find a tutorial.
Thanks

---

### Post by BrandonBan6 on 2009-02-06
Is there a readme file? Usually specific instructions are included there, but generally you have to open terminal and type:

```

cd extracted_file_path
./configure
make
sudo make install

```

---

### Post by GARoss on 2009-02-06
Thanks.
The read me says; 
*Run ./cinelerra from this directory.  That's it.*
I have this on my Desktop &, to be honest, I'm unable to navigate there in the terminal. 
The terminal open & says; 
*george@george-desktop:~$*
after the $ sign I typed, *cd cinelerra-4-ubuntu-amd64*, which is the name of the folder. It responds, no such folder. I tried several other combinations that failed, too. As I said, I'm a newbe.
Need some help.
Thanks again,
George

---

### Post by BrandonBan6 on 2009-02-06
Oh, okay. 

Well the "george@george-desktop:~$" means you are sitting in your home directory (i.e. /home/george).

So in terminal type:
```
cd Desktop/cinelerra-4-ubuntu-amd64
```
That command says "change directory" to /home/george/Desktop/cinelerra-4-ubuntu-amd64.

Now type:
```
sudo ./cinelerra
```

and it should kick off the install...let me know if not, we can work from there.

---

### Post by GARoss on 2009-02-06
We're working! I moved the entire folder to my home folder & then typed,
*george@george-desktop:~$ cd cinelerra-4-ubuntu-amd64*, it worked. Then,
george@george-desktop:~/cinelerra-4-ubuntu-amd64$ ./cinelerra, & I about leaped out of my seat when the program started! I expected it to go through an install.
Thanks. This will be simpler from now on.
One interesting thing is an error that says,
 
**The following error occurred:**
[I]MWindow::init_shim:/proc/sys/kernel/shmmax is 0x2000000.
 It should be at least 0x7fffffff for Cinelerra[/I].

What's that?
George

---

### Post by BrandonBan6 on 2009-02-06
Always remember, google is your friend with any error code :) 

I found this site:
[http://ubuntuforums.org/archive/index.php/t-419690.html](http://ubuntuforums.org/archive/index.php/t-419690.html)

which states:
in terminal type
```
sudo gedit /etc/sysctl.conf
```

and added these lines:
# make cinelerra happy
kernel.shmmax = 2147483647

save file and quit gedit.

---

### Post by GARoss on 2009-02-06
BrandonBan6, I'll be a pro before long! Getting lots of experience, here.
I can say, as I'm sure most newbe's would, this freaks me out, but, oddly enough, its starting making sense.
As for Google; I've used it 1000 times this week!
Thanks

---

### Post by BrandonBan6 on 2009-02-06
> **GARoss said:**
> BrandonBan6, I'll be a pro before long! Getting lots of experience, here.
I can say, as I'm sure most newbe's would, this freaks me out, but, oddly enough, its starting making sense.
As for Google; I've used it 1000 times this week!
Thanks

haha, we all are!! Good luck to you sir.

---

