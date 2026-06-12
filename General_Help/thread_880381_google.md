---
title: "google?"
date: 2008-08-04
forum: General Help
---

### Post by shortribs on 2008-08-04
I just downloaded/installed 8.04 on my computer and now while browsing the web I tried to go to google. It would not load the web page so i tried other websites and most worked. Live.com like google did not, though. So now I am wondering why won't google or live work?

---

### Post by K2712 on 2008-08-05
Your ISP may be having DNS issues.  See if you can access google from here:

[http://72.14.207.99](http://72.14.207.99)

---

### Post by shortribs on 2008-08-05
The link works but when i search it doesn't work... I've just been trying to use other engines.

---

### Post by K2712 on 2008-08-05
It seems that you are having DNS issues.  Can you access your modem/router via a browser?

Or you could try OpenDns:

[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

---

### Post by dexter.deepak on 2008-08-05
i think editing /etc/hosts would do :
```
sudo gedit /etc/hosts
```
now add this line :
```
72.14.207.99     google.com
```

---

### Post by hyper_ch on 2008-08-05
or you might have issues with IPv6 (if surfing generally is very slow)

---

### Post by shortribs on 2008-08-05
Ok well thanks to everyone who tried to help but I don't have any idea now how to have root access so i can change the dns servers. So if anyone can tell me how to get root access it would b greatly appreciated.

---

### Post by dexter.deepak on 2008-08-05
prepend "sudo" to your commands.
like :
cat /etc/hosts , opens the file as a normal user
sudo cat /etc/hosts opens it as root.

---

### Post by K2712 on 2008-08-05
The command sudo grants temporary root access.  Any time you use sudo it will prompt you for your password, it's the same as the one you use to login.

Now, open a terminal:   Panel menu->System Tools->Terminal

and copy/paste the following commands in order:

```
sudo cp /etc/resolv.conf /etc/resolv.conf.auto
```
```
sudo gedit /etc/dhcp3/dhclient.conf
```

Now a text-editor is going to open up.  Copy the following line and paste it at the very end of the file.
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
Save the file and close it.

Last command:
```
sudo ifdown eth0 && sudo ifup eth0
```

---

### Post by shortribs on 2008-08-05
dexter-
I was using the command: sudo network-admin     that opened the network settings but when i switch to the dns tab, i can't click any of the buttons.. not even unlock. I apologize for not being so clear. I don't know why unlock would be an inaccesible button.

---

### Post by dexter.deepak on 2008-08-05
@shortribs,
before trying K2712's solution, i request you to please try my solution...i just want to confirm if it works.
thanks.

---

### Post by shortribs on 2008-08-05
K2712-
I did everythimg you said but google still won't load..

---

### Post by shortribs on 2008-08-05
dexter-
I tried yours and K2712's solutions but neither worked. I'm probably doing something wrong as this is only my second day using ubuntu. I'm used to xp professional.

---

### Post by shortribs on 2008-08-05
Sorry for triple post, but I've figured it out for myself, I just fidgeted with user settings and i was finally able to access the unlock button for network dns servers.. Thanks to all for help. I appreciate the responses.

---

### Post by dexter.deepak on 2008-08-05
i dont think you should face problem here.
type this is the terminal :
```
sudo bash
cp /etc/hosts /etc/hosts.bak
echo "72.14.207.99     www.google.com" >> /etc/hosts    

```

---

### Post by shortribs on 2008-08-05
Ok, I was wrong about doing it myself.. I got to the network dns servers but my changes didn't work. However, thanks to dexter.deepak google actually loads and i can search.. NICE! So, one last question for dexter: Will this change save and stay that way or will I have to input those commands every time i boot if i want to use google? I lied, 2 last questions.. What about other websites that won't load.. like live.com?

---

### Post by shortribs on 2008-08-05
Well google is working.. but many other sites still won't load. for example: live.com and newegg.com. Does anyone know ow to fix it so all work?

---

### Post by hyper_ch on 2008-08-06
post
```

cat /etc/resolv.conf

```

---

### Post by shortribs on 2008-08-06
hyper_ch: thank you so much, the pages that weren't working now are. They just take a little longer to load. Thanks for the easy solution.

---

### Post by dexter.deepak on 2008-08-09
> **shortribs said:**
> Well google is working.. but many other sites still won't load. for example: live.com and newegg.com. Does anyone know ow to fix it so all work?

i am sorry, got too busy to respond.
you can use all the sites, with their ip addresses.
just try this in terminal :```
ping live.com
```
you can also try any other site of your choice. this gives you the ip address of the server (something in the brackets):
```
 ping yahoo.com
PING yahoo.com (206.190.60.37) 56(84) bytes of data.

```

now you can replace the ip address like for yahoo :
```
echo "206.190.60.37     www.yahoo.com" >> /etc/hosts
```

---

