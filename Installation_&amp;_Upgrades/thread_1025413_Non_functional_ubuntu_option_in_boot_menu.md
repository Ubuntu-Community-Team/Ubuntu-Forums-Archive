---
title: "Non functional ubuntu option in boot menu"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by adisomani on 2008-12-30
Hi,

While installing ubuntu on my vista enabled machine, I accidently shut down my machine. Now when I turn on my machine ,I see the following two OS to boot from :
1. Vista which works fine.
2. ubuntu (this is exactly what appeaers, no other 3-4 options that appear on successful installation.)

when I select ubuntu, a blank screen appears and it persists.
How to fix this?

Thanks,
Aditya Somani

---

### Post by sleepyjon on 2008-12-30
Just boot the live cd and reinstall on the same partition.

---

### Post by TomasJancik on 2008-12-30
at what point of installation did the machine shut down?
maybe you'll only need to fix grub

---

### Post by adisomani on 2008-12-30
The machine shut down after I selected a partition to be resized for installation.
But when I restarted no new partition was actually created.

Afterwards, I tried to reinstall it again but this time it chose some other partition for resizing and was installed successfully. 

Fixing the GRUB also didn't help. I restored it using my vista CD (using fixmbr) , but nothing changed. Only the successful installation got removed.

---

### Post by adisomani on 2008-12-30
How do I install it on the same partition? I tried reinstalling it but it option is still there. The installation resulted in :

On booting a screen appears with the following options :

ubuntu 8.10
..2-3 more options of ubuntu including recovery
---Other OS:
Vista Longhorn Loader
Windows XP embedded

when I select Vista Longhorn Loader the original screen with the 2 options :
Microsoft Vista
ubuntu

reappear.

---

### Post by caljohnsmith on 2008-12-30
It sounds like you originally had a Wubi install of Ubuntu, meaning you had Ubuntu installed inside of Windows; but now you might have Ubuntu installed to its own partition. In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by adisomani on 2008-12-30
Yes, you seem correct. Before installing full fledged UBUNTU I just installed it from inside of windows. But then I aborted it in between.

I tried running your script, but its giving some errors.
While the first few errors (till line 99) are resolved by removing the blank line, I couldn't see any problem with the 
last one. What is the problem?

Here are the errors.

```
ubuntu@ubuntu:~/Desktop$ sudo bash boot_info_script1.txt 
: command not foundxt: line 50: 
: command not foundxt: line 55: 
: command not foundxt: line 69: 
: command not foundxt: line 84: 
: command not foundxt: line 98: 
: command not foundxt: line 99: 
'oot_info_script1.txt: line 101: syntax error near unexpected token `{
'oot_info_script1.txt: line 101: `titlebar_gen () {

```

---

### Post by caljohnsmith on 2008-12-30
I'm not sure what the problem is, because the script has been running OK for me and everyone else who has downloaded it in the last couple of days. How did you download it? Did you use the wget command or did you manually copy/paste it? How about right-clicking [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your browser, choose "save target as", then save the script to your Ubuntu desktop and run it. See if that works.

---

