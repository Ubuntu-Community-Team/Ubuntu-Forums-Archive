---
title: "software sources will not let me import a key file"
date: 2008-09-26
forum: General Help
---

### Post by mattlloyd on 2008-09-26
First off, I'm new to Ubuntu... and loving it!  That said, assume I'm a moron when giving advice :)

I'm trying to get an old WUSB11 linksys wireless adapter to work with hardy... I decided to try both the Windows Wireless Driver route and the Cafuego driver route... same issue both times.
With the Windows wireless driver, it let me install it, then after a reboot it closes immediately after opening :(

With Cafuego (my first choice if it will work), when I try to run apt-get update I get the following error

W: GPG error: [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) hardy-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81600957AF425CB5

I tried to add the key in System>Admin>Software Sources... same issues as with Windows Wireless Driver; it closes as soon as I press the Add Key button.

Suggestions?

---

### Post by plucky on 2008-09-27
> Suggestions? 

Add these two lines to your sources.list assuming you are using Hardy.
```
deb     http://ubuntu.cafuego.net/ hardy-cafuego all
deb-src http://ubuntu.cafuego.net/ hardy-cafuego all
```

Click on the [This Link](http://ubuntu.cafuego.net/) will open the home page.
On the right is the **GPG signatures:** click on [color=red]**AF425CB5**[/color] will open GPG Public Key block.Go to **File** and **Save Page as**. will save your page as cafuego.gpg on your desktop or wherever your downloads go.

The open **Software Sources** and go to **Authentication** and import the key file from your desktop.
Reload and you should be good to go.

Good Luck

---

### Post by mattlloyd on 2008-09-27
same problem as before... when I click on Import Key File, the prog closes :(

---

### Post by plucky on 2008-09-28
> **mattlloyd said:**
> same problem as before... when I click on Import Key File, the prog closes :(

Are you sure it hasn't added it to the authentication window?



If not,Open a terminal and ```
cd <location of key file>
sudo apt-key add <name of file>
sudo apt-get update
```

Substitute the directory for <location of key file> 
To make sure you are in the right directory input into the terminal **ls** and it should list your file.

Good Luck

---

### Post by inaho on 2008-10-08
Hi,
the problem is solved if you use the follow command:

 sudo wget [http://debian.cafuego.net/cafuego.gpg](http://debian.cafuego.net/cafuego.gpg) -O- | sudo apt-key add -

the page with the key is called cafuego.gpg and not AF425CB5.gpg

bye

---

