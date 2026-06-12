---
title: "Active Directory"
date: 2007-08-29
forum: Georgia Team - US
---

### Post by dwilliams07 on 2007-08-29
Hello,

I am new to Ubuntu (Linux in general) but I have been very impressed with it.  I'm trying to prove to my co-workers that it can be used in our Active Director Domain.  Can somebody please tell me how to join an Ubuntu 7.04 desktop to an AD domain?  I recently tried a program named Sadms but I keep getting error messages.  I just need to a clean and easy way to do this.  I'm trying to show folks that there is a better and cheaper way.  Please help!!

---

### Post by siafulinux on 2007-08-30
Hi dwilliams!

Congrats on joining the Ubuntu/Linux world!

Unfortunately I have not worked with Active Directory Domain servers and so do not have any experience with it. I did a bit of research and found some guides that may be able to help you with your problem. 

I am assuming you are trying to access the already established Windows Active Directory Domain Server? If not, I also looked into some guides into setting up an Ubuntu based server instead.

---
Now, on to accessing a windows ADD Server.

The first guide is fairly short and to the point and can be found at [http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain](http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain)
Though dealing with Ubuntu 5.10 I am certain it will work for newer versions of Ubuntu as well.

It too, like SADMS, uses Samba and Kerberos, but might be a more hands on alternative to using SADMS directly. 

I also found a longer guide at [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

Also give us the errors you are receiving while trying to set this up using SADMS. It'll give us a better idea of what we are looking at.

---
On the other hand if you are trying to set up a server with Ubuntu to allow your Windows (and other / Linux) machines to be authenticated from it you can use the Lightweight Directory Access Protocol (LDAP). Actually OpenLDAP. Active Directory Domain is in fact a Windows implementation of LDAP.

Again I found two guides that could be the answer, but you may want to get a cup of coffee, crack your knuckles and get ready for a good, fairly longish read.

[http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap)

This second is a little less involved it seems:
[http://www.islandlinux.org/HOWTO/openldap_samba.html](http://www.islandlinux.org/HOWTO/openldap_samba.html)

---

Unfortunately it doesn't seem like there is any gui / easier method for this, but I could be very wrong here. Anybody else who knows more about this, please join in. 

Keep us informed about any successes or failures.
And once again, good to have you with us!
Jean-Claude

---

### Post by rsmereka on 2007-09-04
Hi  Jean-Claude,

Thanks a lot for your very informative post. I too, like dwilliams am trying to introduce Linux into my companies business and was looking for a howto in regards to connecting a Ubuntu desktop to a Windows 2003 active directory domain. I started off using:

[https://wiki.ubuntu.com/JoinWindowsDomain](https://wiki.ubuntu.com/JoinWindowsDomain)

I had no success with this guide because the guide tells me to run a series of diagnostics on the 'sadms' configuration. The Kerberos diagnostic was failing telling me that Kerberos was not configured and the list of realms it spit out did not make sense for my environment.

Instead of trying to debug the current situation, I searched the forums and found your post. As per your suggestion, I used the guide:

[http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain](http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain)

and although is is a lot more manual and prone to error due to mis-typing, it worked the first time for me.

I noticed only one mistake in the guide where is refers to the file /etc/nsswitch and it shoud be /etc/nsswitch.conf. An easily correctable error.

Once again, thanks for the great post and keep up the good work=D>

Rick

---

### Post by siafulinux on 2007-09-04
Hi Rick

I too am trying to get the company I work for to use Linux, but so far it's been a no go. They don't want to even hear about it :-). As far as I know they don't use any form of Active Directory though.

Needless to say I've had no experience with this at all. Seen it here and there before but never had a reason to actually try it out. I was still going to attempt putting a test together of some sort, but I have no Windows or Active Directory Server to test with. It would've been purely Linux based which would've defeated the purpose I guess.

So, thank you for letting us know that this guide worked and for pointing out the error! It is much appreciated.

Good luck with the company, I hope they have the openness to see how Linux can benefit them.

Jean-Claude

---

### Post by dwilliams07 on 2007-09-11
Thanks to everyone for the advice.  I'm sorry for not responding sooner.  The error message I received was similar to Rick's (Kerberos).  At any rate, I'm going to try the guide in Jean-Claude's post and follow up.  I cannot wait to get back to work and try this.  The crazy thing is, when I even mention Linux folks look at me like I'm crazy.  I'm amazed at how using the other operating system has made people not even want to try something different.  It's like they're brainwashed.  I'm studying for the Linux+ certification now and I am just so happy to be learning something new.  Thanks again for your help.

---

### Post by siafulinux on 2007-09-12
You are welcome, hope it works for you. 

I think we all get those looks from people, especially at work. However, I just recently got a long time friend and user of MAC to try Linux after buying a Windows Vista based laptop with two partitions. (It came that way, I don't know why.).

His response after I installed Kubuntu for him and he had some time with it was... and I quote, "This thing is pretty much awesome!!  It's about 100 times faster and even easier to use" and "...I am sorry that I didn't hop on this train years ago. Thanks for introducing it to me". Success! 

So don't give up, some will get the idea and love it like the rest of us.

Good luck with the Linux+!

Jean-Claude

---

### Post by rsmereka on 2007-09-12
Hi  Jean-Claude.

Speaking of wasted partitions. I recently got a Dell XPS M1710 with Vista Business. It came with four paritions. That's right, count em, four partitions:
1. the standard Dell 48mb partition right at the front of the drive that has no drive letter. Every Dell has one of these.
2. The main data drive (NTFS)
3. A drive labeled 'recovery' with some Vista OS files on it
4. A small partition wasted, not assigned to any drive

I could not believe this. I wanted to put Ubuntu 7.04 on this laptop and I cannot now unless:

a. someone knows a way around the four partition limit on any one physical drive
b. someone knows how to consolidate these partitions without me wiping and re-installing.

I guess if I get mad enough I may rip the whole thing apart and consolidate Vista onto a single partition.

Rick

---

### Post by siafulinux on 2007-09-13
Hi Rick

I replied to this post at [http://ubuntuforums.org/showthread.php?p=3357032]("http://ubuntuforums.org/showthread.php?p=3357032") as it was getting off the topic of the original thread. 

Jean-Claude

---

### Post by johnbradbury on 2007-10-01
rsmereka you'll need to use disk manager do delete one of the existing partitions. Obviously you'll need to transfer any data off that partition first.

Once that's done create a new extended partition [not primary]. Within an extended partition you can then create numerous logical partitions. This is the only way around the four partition rule.

---

### Post by Monah on 2007-10-15
hello, i'm from Ukraine!

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)


> root@linuxwork:~# ping win2k3.lab.example.com

PING win2k3.lab.example.com (10.0.0.1) 56(84) bytes of data.
64 bytes from win2k3.lab.example.com (10.0.0.1): icmp_seq=1 ttl=128 time=0.176ms

It has passed normally!


> file: /etc/default/ntpdate
 
# servers to check
NTPSERVERS="win2k3.lab.example.com"
# additional options for ntpdate
NTPOPTIONS="-u"

root@linuxwork:~# /etc/init.d/ntpdate restart

I carry out

> root@linuxwork:~# /etc/init.d/ntpdate restart

server to me writes!

bash: /etc/init.d/ntpdate: No such file or directory

All has put and &#1079; specified!

---

