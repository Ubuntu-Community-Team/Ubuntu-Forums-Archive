---
title: "NOOB HELP!!!  GNOME problems after LOG IN!"
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by unoobu on 2006-05-02
Dear Linux Community,

I am running Ubuntu on my Inspiron 8600 laptop.  I just updated the kernel, and rebooted. After log in, I get this error message:

"Could not look up internet address for .
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
to the file /etc/hosts."

Then I have two buttons asking me to log in anyway, or try again...

The problem is, that with this error I am unable to run SYNAPSE, Update Manager, Users and Groups, Wireless Configuration, etc...

Peace,

uNOOBu

---

### Post by joe_gosse on 2006-05-02
Have you looked at the file /etc/hosts ?

Mine looks like this and seems to work find. The solutions I've found through google for this problem involve making some changes to that file.
> 127.0.0.1 localhost.localdomain localhost joelaptop
192.168.0.105 joelaptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by unoobu on 2006-05-02
I am a noob, I dunno?  Also, I don't think there is a root account.  Is this possible?  When I try to log in as root, it says invalid name or user password...  I never set a root password, just a main user password...  as far as I know...

Oh, and I should be editing these in gedit right?


Okay this is my /etc/hosts file

127.0.0.1 localhost.localdomain localhost 

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by unoobu on 2006-05-02
Nevermind, I found another thread on this after all...

It is quite complicated, and I don't fully understand...  So I just took the lamer way out and reinstalled...

but I did learn a command or two in the process

---

### Post by Hugin on 2006-05-03
The first account you created during the install has sudo use privlages

What that means is when you type "sudo gedit /etc/hosts" in a terminal it will open the /etc/hosts file in gedit with root privlages so you can change it.  

You will be asked for your password when you run a command as sudo it is just your normal ubuntu login password.

---

