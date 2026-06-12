---
title: "Install Samba 3.0.34 from Binary"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by ewendt on 2009-06-25
Im trying to install Samba 3.0.34 onto my Ubuntu 9.04 system from a binary package I've downloaded. i am using this version because the version that comes with Ubuntu, 3.3.2, from what i have read will not integrate with Likewise correctly for Active directory authentication. i download the source conigure it complie then install. but when i try to confirm the install by running smbd -V to check the version it says that it is not installed and to use the apt-get command to install it. it appears that the samba files are in the /usr/local directory. can anyone help me out.

---

### Post by Daimones on 2009-07-01
I'm in the exact same boat, I have noticed that samba has in fact installed the command in /etc/init.d to start the services but when attempting to start them it returns nothing.

Same problem if I go to /usr/local/sbin/smbd or /usr/local/sbin/nmbd The commands work but nothing starts or anything.

Anyone have an ideas, if you need more info I will gladly provide.

---

### Post by ewendt on 2009-07-02
well i try installing 3.3.2 instead now and it seems to be working fine so far but I haven't actually tested the entire thing yet. but im able to access my shares from windows and as long as i give my domain\user rights to the share it works correctly i need to try doing this by group but i will see where this gets me

---

### Post by Daimones on 2009-07-02
Using likewise it worked? Whenever I install likewise my wbinfo starts failing, I can configure it fine with just winbind, but when likewise installs it doesn't work anymore. What steps did you use to install likewise?

---

### Post by ewendt on 2009-07-02
i simply installed likewise from the synaptic package manager joined the domain then installed samaba and configured it to use ADS authentication pointed it towards my domain and made sure it had encrypted passwords.

---

### Post by Daimones on 2009-07-02
Hmm, you make it sound simple hah, I have been trying that for days to no avail. So here are a couple of questions for ya:

Did you make any changes to kerberos, PAM, or nsswitch?

Did you use likewise 4 or 5?

Also would you maybe post your smb.conf?

---

### Post by ewendt on 2009-07-02
lol sorry
I am using likewise 5
i have not done any editing to my kerberose, PAM, or nsswitch files
sorry for security reasons i cannot post the changes to the smb.conf file but i can tell you i used SWAT to do all my editing.
just in case ou don't know what it is swat is a editing program that uses and web browser to edit your smb.conf file. i found that it made everything simpler and i gives easy help to each field. you have to login as root to it though or u wont have any editing permissions.

---

### Post by Daimones on 2009-07-02
Well you don't need to post your important info, you could use xx.xxx.xxx for ip addresses and YOURDOMAINNAME for domains, but alas could you tell me if you made more edits than the following?


security = ads
workgroup = SHORTDOMAINNAME
realm = YOURDOMAINNAME.COM

idmap backend = lwicompat_v4      I tried both lwopen and lwicompat_v4
idmap gid = 50-9999999999
idmap uid = 50-9999999999

I basically followed the final post of this 

[http://ubuntuforums.org/showthread.php?p=5399487#post5399487](http://ubuntuforums.org/showthread.php?p=5399487#post5399487)

---

### Post by ewendt on 2009-07-02
I made those same edits but......lol i just found out my likewise is jacked up lol. i hadn't logged onto my machine using AD credentials till now since the install and configuration of my Samba server so now we are back to square one with that

---

### Post by Daimones on 2009-07-02
Ouch sad news:( Well I will keep trying and will gladly let you know if I find anything, I'm still holding onto the need for samba 3.0.34 being the issue, based on what I have read online.

Hopefully someone will pop their head in here and help us out, otherwise I'll keep ya posted with any progress I make.

---

### Post by ewendt on 2009-07-02
yea im going to agree with you on this issue im going to hold for 3.0.34 as well since likewise does specifically call for 3.0.x i will also keep any new developments that i or my co-workers come up with posted on here

---

### Post by Daimones on 2009-07-02
Well I've come to one conclusion, in likewise5 lwopen.so doesn't actually exist, so creating a link and using it as your backend is useless. Also the lwicompat_v4.so is actually located in /usr/lib/likewise-open5/lwicompat_v4.so

So you probably want to create your symbolic links to that spot, rather than the locations most guides give you.

---

### Post by Daimones on 2009-07-06
I have tried so many things as far as getting 3.0.34 installed from binary to no avail, can anyone shed some light on the topic? Based on the articles I read online that should fix the problem we are having.

I just don't know what to try anymore.

---

### Post by ewendt on 2009-07-22
Well what we have submited to doing for now here is using ssh to transfer files from a mounted share point to the linux system. so basicaly what we do is ssh or telnet into the system mount a windows share and copy files from that share where they need to go so for now that is what works for us. i did some reading and it appears the likewise is developing their own file share program that will be baised off samaba like the authenticator is but the offical release wont be untill september last i looked. and we wont test with an RC because we need stability and relyability right now but if someone were to test this and let me know how good it works so i can lookinto it more after the final release is issued would be apreciated.

---

