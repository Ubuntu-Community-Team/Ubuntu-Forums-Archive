---
title: "How to connect a laptop to a desktop?"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by eeried on 2005-07-21
Hello,

I'm thinking of "building" a local network including a desktop with Linux installed and a laptop with ubuntu installed.

I suppose  I first need to get a cable to link the two computers. Both computers have  ethernet cards.

Now when I installed Ubuntu,  I couldn't set up the network since I didn't have a cable.

Can you tell me what steps I should follow, as I have never done this before. Is there anything specific to Ubuntu, or is there a good Howto you would recommend?

Many thanks in advance,

---

### Post by SFN on 2005-07-21
Well, how to build a network is a deep topic. To get two computers networked together, ideally you want a switch between the two computers. One cable goes from the laptop network card to the switch and one cable goes from the desktop network card to the switch.

If you don't have the money/time/inclination to go through that, you can run one crossover cable between the laptop network card and the desktop network card. That's about as simple a network as you can have.

Using a switch will be a lot better, though.

---

### Post by s_p_a_r_k_y on 2005-07-21
[QUOTE=eeried]Hello,

I'm thinking of "building" a local network including a desktop with Linux installed and a laptop with ubuntu installed.

I suppose  I first need to get a cable to link the two computers. Both computers have  ethernet cards.

Now when I installed Ubuntu,  I couldn't set up the network since I didn't have a cable.

Can you tell me what steps I should follow, as I have never done this before. Is there anything specific to Ubuntu, or is there a good Howto you would recommend?

Many thanks in advance,[/QUOTE]

If you want a direct link, then you will need to purchase a "cross over cable" otherwise that wont work. I recommend getting a switch, and plugging both into the switch. If you get the switch solution, then purchase 2 normal lan cables and plug em in.

Once they are both plugged in via switch or cross over they have to be on the same network with different addresses.

example desktop:
```

sudo ifconfig eth0 192.168.0.1

```
example laptop:
```

sudo ifconfig eth0 192.168.0.2

```
They should both now have the same network. Then try to ping each other
from the desktop:
```

ping 192.168.0.2

```
If you see lines starting with
"64 bytes from" then it should be succesful.

Then if you want to share files you will want to setup samba or NIS. I think samba is easier and will let your Windows buddies bring their laptops over and also get access to the files.

```

sudo apt-get install samba

```
then once thats done setup a share
```

sudo nano /etc/samba/smb.conf

```
then add something like this, replacing the path with somewhere where you want to share files from
```

[myShareName]
     path = /mySharedFiles
     browseable = yes
     writeable = yes

```
Now both desktop and laptop will need to have samba user accounts...
```

suda smbpasswd -a username
sudo /etc/init.d/samba restart

```
Now each comp should have a user account and a shared folder. Time to give it a spin
```

sudo mount -t smbfs //192.168.0.1/myShareName /where/Iwant/To/Mount -o username=myusername

```
It'll prompt for the password. If you want to have a netbios name like desktop/laptop instead of 192.168.0.1/2 then add "netbios name = bart" in the "[global]" section. Give each a different name. My laptop's name is bart as all my computers are named after a simpson character. From now on you can use sudo mount -t smbfs //computername/myShare.... instead of writing that damned IP!

Once its mounted, you should see it when you enter the "df" command.

Try copying some files to it...

enjoy

---

### Post by sooqing on 2005-07-28
well.. since both machines are running linux.. use NFS to share files..

---

### Post by eeried on 2005-08-02
Many thanks for your replies!

NB: I don't want any connection to Windows (boo)  ;-)   even though I have installed Ubuntu dual-boot alongside preinstalled winxp on the laptop. 

Am I right in thinking Samba is only needed if you want to connect a windows computer and a Linux computer?

I've also found some interesting doc on how to set up a linux network from this Web site 
[http://www.aboutdebian.com/index.htm](http://www.aboutdebian.com/index.htm)

But your explanations make things easier for a total network newbie like me!

One question though: What's NFS, recommended by sooqing?

---

### Post by s_p_a_r_k_y on 2005-08-03
um I recommended samba bc its the only thing I've had experience with. You can network Macs, Linux, and Windows with samba, currently I have 2 linux machines and one windows at home all talking to eachother over samba. I think its quite easy to setup and its all I really know. NFS might be worth a try but I can't talk you through that...although I should learn it myself one of these days.

---

