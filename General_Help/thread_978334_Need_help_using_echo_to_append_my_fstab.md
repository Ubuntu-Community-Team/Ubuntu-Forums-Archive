---
title: "Need help using echo to append my fstab"
date: 2008-11-11
forum: General Help
---

### Post by diablo75 on 2008-11-11
I'm trying to write up a script that will install a lot of different software (Ubuntu restricted extras, skype, google earth, Virtual Box).  With Virtualbox, you have to add a line of text in order to grant VB access to your USB ports.  I've been told to do the following:

```
sudo echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```

However, I get:

```
bash: /etc/fstab: Permission denied. 
```

It doesn't even ask me to type in my admin password when I try to do this?  Am I doing something wrong, or is there another way to go about doing this?

---

### Post by tbielawa on 2008-11-11
sudo su -c "echo 'bla2bl2abla2' >> randomfile"


You might have better luck with something similar to that


It didn't work the way you tried it because of how bash handles input and output. What you actually did was echo as root, but when you used ">>" it was run as you again because your shell breaks the commands up.

---

### Post by geirha on 2008-11-11
>> is interpreted by the shell, not echo. And only echo has elevated priviledges, not the shell. The tee command is useful for such purposes though
```
echo "line to be added" | sudo tee -a /etc/fstab
```

---

### Post by diablo75 on 2008-11-11
> **tbielawa said:**
> sudo su -c "echo 'bla2bl2abla2' >> randomfile"



That worked perfectly!  


> **geirha said:**
> >> is interpreted by the shell, not echo. And only echo has elevated priviledges, not the shell. The tee command is useful for such purposes though
```
echo "line to be added" | sudo tee -a /etc/fstab
```

I think for my purposes (I am writing a blog about this experiment for people to read, showing them some things about the Terminal that I've not discussed before) I shall use this command instead, simply because it includes a | pipe, which can be quite handy for things like running lspci and piping the output through grep to tease out lines that have a matching keyword.  

Thank you both for your help!

---

