---
title: "Flash Player"
date: 2008-08-10
forum: General Help
---

### Post by Thardmann on 2008-08-10
Hello.

Im really new at ubuntu, and now im having a problem with Flash. I cant get flash sites working, and i cant get the adobe flash player downloaded. I have tryed it in alle the 3 differend linux types, but none worked..

Someone? :D

---

### Post by NilsE on 2008-08-10
Have you tried to install flashplugin-nonfree from the Synaptic package manager?

---

### Post by niyonk on 2008-08-10
execute this command 'sudo apt-get install flashplugin-nonfree' in terminal to install Adobe's flash Player plugin :)

Read [here]("https://help.ubuntu.com/community/RestrictedFormats/Flash") for more

---

### Post by Thardmann on 2008-08-10
evrytime i try to use the Synaptic it says this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by CKyle22 on 2008-08-10
Use apt-get instead.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Thardmann on 2008-08-10
when i try that, it asks me for a password? and i cant write anything :S
and it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by CKyle22 on 2008-08-10
Hehe yes you can you just can't see it. Type your user password and press enter. You won't see the password being typed, don't worry.

---

### Post by wesley_of_course on 2008-08-10
> **Thardmann said:**
> evrytime i try to use the Synaptic it says this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Evening ! Dug around and found this ;
 Applications -> Accessories -> Terminal
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
[http://ubuntuforums.org/archive/index.php/t-653495.html](http://ubuntuforums.org/archive/index.php/t-653495.html)

Can't hurt and hope it helps .

---

### Post by Thardmann on 2008-08-10
it says :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by niyonk on 2008-08-10
run 'cd /var/lib/dpkg/updates' in terminal to go to the updates directory
run 'sudo rm *' to remove all updates you downloaded..

It seems that error is because you have some corrupted updates 

[source]("http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/")

---

### Post by CKyle22 on 2008-08-10
> **Thardmann said:**
> it says :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.So try it and see what happens.

---

### Post by Thardmann on 2008-08-10
okay. its runnigns something now XD

---

### Post by Thardmann on 2008-08-10
Its still ******  :S

---

### Post by CKyle22 on 2008-08-10
What's it say?

---

### Post by Thardmann on 2008-08-10
that i cant use that command "dpkg --configure -a" , becouse only some superuser can do that? 

but i am admin :S

---

### Post by Thardmann on 2008-08-10
now its works. but it freeze somewhere..
this is the last thing it says:

update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
Sætter language-pack-en-base (1:7.10+20080205) op...
Generating locales...
  en_AU.UTF-8...

---

### Post by abredin on 2008-08-12
this happened to me, try "sudo dpkg --configure -a"

---

