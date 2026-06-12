---
title: "sudo-problem"
date: 2005-11-12
forum: General Help
---

### Post by series on 2005-11-12
Hello. I have the following problem:

I compiled a custom kernel and when I want to run a program from the panel-menu that requires root-privileges, this happens: "Failed to run childprocess 'gksudo' (The file does not exist)".
Now I wonder how do I change this so that I get prompted for my root password instead?

---

### Post by adwait on 2005-11-12
When it says gksudo, the file doesn't exist, I think it means that gksudo is not installed at all. Try installing it with
```
sudo apt-get install gksudo
```
gksudo = GUI for sudo.

---

### Post by series on 2005-11-13
The package does not exist, apt-get says.

---

### Post by adwait on 2005-11-13
try
```
sudo apt-get install gnome-sudo
```

---

