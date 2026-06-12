---
title: "Change download servers from command line?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by dasunsrule32 on 2009-10-30
How do I change the whole sources.list to a different update server? I want to change from the US server to one in utah that is blazing fast. How do I do this from the CLI? I am running Server 9.04 and want to upgrade, without using do-release-upgrade. Thanks.

---

### Post by scragar on 2009-10-30
Use a text based editor to edit the sources file.
```
sudo nano /etc/apt/sources.list
```
Ctrl+o to save
Ctrl+X to exit.

---

### Post by dasunsrule32 on 2009-10-30
I know this, i want to have the file scanned and then replace all the existing URL's for the US server to the Utah server. Thanks though.

---

### Post by scragar on 2009-10-30
Well you can comment out the current server and remove the comment from the other server, but it's a bit of a risk really.
```

sudo sed -i 's/^[^#]/#/' /etc/apt/sources.list
echo "NEW URL" | sudo tee -a /etc/apt/sources.list
```

Much safer to do it by hand.

---

### Post by dasunsrule32 on 2009-10-30
I ended up modifying your sed command, worked great. Thanks.

---

