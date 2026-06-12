---
title: "Getting ADSL to auto-connect on boot"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by Confused Fishcake on 2005-11-05
I finally got my internet working on ubuntu, but i have to run "pon ADSL" in terminal to start the connection. Is there any way I can get it to do this at boot?

---

### Post by adwait on 2005-11-05
Well, when you setup the connection using pppoeconf, if gives you an option to do so. Rerun it and select that option. If not, you can type whatever commands you use to connect in a file. Make it executable with
```
chmod +x <filename> 
```
Move it to /etc/init.d using
```
sudo mv <filename> /etc/init.d/
```
then run
```
sudo rcconf
```

Check the box against the file that you created using spacebar and ok your way out.

---

### Post by Confused Fishcake on 2005-11-05
Well, the first two commands work, but I get an error running rcconf - no command called that. Do I need to install anything first?

---

### Post by Confused Fishcake on 2005-11-05
Oh, it is a package, got it to work perfectly now :). Completetly unimprotant, but the time synchronisation to ubuntu.com always fails. Is there any reason why this happens? Can I fix it? If not, can I turn off the time check because it look ugly when it fails. Thanks for your help, though.

---

### Post by adwait on 2005-11-05
I don't really know why the sync fails even though the connection to the internet is made before it, but fact remains it fails in most cases using ADSL connections. Anyway, to turn it off use
```
sudo update-rc.d -f ntpdate remove
```

---

