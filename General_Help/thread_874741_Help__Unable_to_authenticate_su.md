---
title: "Help : Unable to authenticate su"
date: 2008-07-30
forum: General Help
---

### Post by Dreamerman on 2008-07-30
Hi. Today I have been unable to authenticate su. The message is -

su: Authentication failure

I am able to get into synaptic using my super password which is the same for su. Entering sudo -i gives me the following message -

sudo: unable to resolve host ubuntu-server

I am able to get into my home LAN & internet, so it is not networking related.

What am I missing ? Please help.

Thanks

---

### Post by iaculallad on 2008-07-30
> **Dreamerman said:**
> Hi. Today I have been unable to authenticate su. The message is -

su: Authentication failure

I am able to get into synaptic using my super password which is the same for su. Entering sudo -i gives me the following message -

sudo: unable to resolve host ubuntu-server

I am able to get into my home LAN & internet, so it is not networking related.

What am I missing ? Please help.

Thanks

Try to post whatever outputs when you issue the command below on your terminal:

```
cat /etc/hosts
```

---

### Post by caljohnsmith on 2008-07-30
Sometimes those type of errors are simply do to the host name for your computer being slightly different in /etc/hosts/ and /etc/hostname. Make sure those two files agree exactly about your host name.

---

### Post by Dreamerman on 2008-07-31
> **iaculallad said:**
> Try to post whatever outputs when you issue the command below on your terminal:

```
cat /etc/hosts
```

Hi. The result as follows:-

cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu-server.TOMKO

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I have disabled IPv6 previously following instruction from the forum as follows:-

1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

Is my problem due to the above ?

Thanks

---

### Post by iaculallad on 2008-07-31
Do include the terminal prompt when you issue the** cat /etc/hosts** command.

i.e:

> **ian@gutsy-gibbon**:~$ cat /etc/hosts
cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 gutsy-gibbon

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Dreamerman on 2008-07-31
> **iaculallad said:**
> Do include the terminal prompt when you issue the** cat /etc/hosts** command.

i.e:

OK. Here goes. Any obvious flaws ?-

master@ubuntu-server:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu-server.TOMKO

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
master@ubuntu-server:~$ 
master@ubuntu-server:~$

---

### Post by iaculallad on 2008-07-31
> **Dreamerman said:**
> OK. Here goes. Any obvious flaws ?-

master@ubuntu-server:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu-server.TOMKO

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
master@ubuntu-server:~$ 
master@ubuntu-server:~$

Yap, it seems that you're /etc/hosts file has the flaw. Edit and change the value.

```
gksudo gedit /etc/hosts
```

and change the line of text:

> 127.0.1.1 ubuntu-server.TOMKO
With

> 127.0.1.1 ubuntu-server

Save and Close the file and test your su.

---

### Post by Dreamerman on 2008-07-31
thanks. do i need to reboot ?

---

### Post by iaculallad on 2008-07-31
> **Dreamerman said:**
> thanks. do i need to reboot ?

No, that's a windoze thing. Just log-off and log back in :)

---

### Post by Dreamerman on 2008-07-31
thx a lot. will do that & post result. BTW, your kid is very cute :-)

---

### Post by Dreamerman on 2008-07-31
> **iaculallad said:**
> No, that's a windoze thing. Just log-off and log back in :)

Hi again. I rebooted & still can't authenticate su. Result as below. Is there anything else I can try ? Thanks

master@ubuntu-server:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu-server

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Dreamerman on 2008-07-31
> **Dreamerman said:**
> Hi again. I rebooted & still can't authenticate su. Result as below. Is there anything else I can try ? Thanks

master@ubuntu-server:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu-server

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

This is another result. Still can't get into su.....sigh.....

master@ubuntu-server:~$ cat /etc/hostname
ubuntu-server

---

### Post by caljohnsmith on 2008-07-31
Did you try "sudo -i" again? Your original problem of it returning the error "sudo: unable to resolve host ubuntu-server" should be solved now that your host name is the same in /etc/hosts and /etc/hostname. That would at least give another clue about your problem.

---

### Post by iaculallad on 2008-07-31
Or maybe you're entering the wrong password when invoking the su command. Remember that using su should require you to input the root password w/c by default is disabled in Ubuntu. Try setting the password for su first:

```
sudo passwd root
```

---

### Post by caljohnsmith on 2008-07-31
> **iaculallad said:**
> Or maybe you're entering the wrong password when invoking the su command. Remember that using su should require you to input the root password w/c by default is disabled in Ubuntu. Try setting the password for su first:

```
sudo passwd root
```
That's a good point, but I think we should respect [Ubuntu's philosopy about the root account]("https://help.ubuntu.com/community/RootSudo") not encourage Dreamerman to set the root password. If he needs to get a root shell, he really should do it with "sudo -i" and not "su". :)

---

### Post by Dreamerman on 2008-08-01
> **caljohnsmith said:**
> Did you try "sudo -i" again? Your original problem of it returning the error "sudo: unable to resolve host ubuntu-server" should be solved now that your host name is the same in /etc/hosts and /etc/hostname. That would at least give another clue about your problem.

Hi. Result as follows. Seems I can authenticate sudo but not su. Any ideas why ? Thanks

master@ubuntu-server:~$ sudo -i
[sudo] password for master: 
root@ubuntu-server:~# exit
logout
master@ubuntu-server:~$ su
Password: 
su: Authentication failure
master@ubuntu-server:~$

---

### Post by iaculallad on 2008-08-01
Try this to resolve your SU problem: Drop on your terminal:

```
sudo -i
```

and input your password. On your successful authentication, you should be dropped to the root terminal. Now, issue the command below:

```
chmod +s /bin/su
```

and exit on the root terminal:

```
exit
```

and test your su

```
su
```

---

### Post by Dreamerman on 2008-08-01
> **iaculallad said:**
> Try this to resolve your SU problem: Drop on your terminal:

```
sudo -i
```

and input your password. On your successful authentication, you should be dropped to the root terminal. Now, issue the command below:

```
chmod +s /bin/su
```

and exit on the root terminal:

```
exit
```

and test your su

```
su
```

Hi. Tried your approach but still the same.

master@ubuntu-server:~$ sudo -i
[sudo] password for master: 
root@ubuntu-server:~# chmod +s /bin/su
root@ubuntu-server:~# exit
logout
master@ubuntu-server:~$ su
Password: 
su: Authentication failure
master@ubuntu-server:~$

---

### Post by iaculallad on 2008-08-01
Try setting the root password and unset it afterwards:

```
sudo passwd
```

and input your password, then try running **su**

If that still fails, Unset the root password:

```
sudo passwd -l root
```

---

### Post by Dreamerman on 2008-08-01
> **iaculallad said:**
> Try setting the root password and unset it afterwards:

```
sudo passwd
```

and input your password, then try running **su**

If that still fails, Unset the root password:

```
sudo passwd -l root
```

*HAIL THE MASTER* Thank you so very much

master@ubuntu-server:~$ sudo passwd
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
master@ubuntu-server:~$ su
Password: 
root@ubuntu-server:/home/master#

---

### Post by caljohnsmith on 2008-08-01
Dreamerman, did you have a chance to read that link I gave about [Ubuntu's policy on root access]("https://help.ubuntu.com/community/RootSudo")? Using "sudo -i" is exactly the same as "su" except it uses your user password, instead of the root password. There is really no reason you should need to use "su" to get a root shell. Iaculallad's method of course works, but it is a workaround that gives the same result as "sudo -i". Is there some special reason you want to use "su" instead of "sudo -i"?

---

### Post by Dreamerman on 2008-08-02
> **caljohnsmith said:**
> Dreamerman, did you have a chance to read that link I gave about [Ubuntu's policy on root access]("https://help.ubuntu.com/community/RootSudo")? Using "sudo -i" is exactly the same as "su" except it uses your user password, instead of the root password. There is really no reason you should need to use "su" to get a root shell. Iaculallad's method of course works, but it is a workaround that gives the same result as "sudo -i". Is there some special reason you want to use "su" instead of "sudo -i"?

Hi thanks. Yes, I have read the rule on root. I managed to solve my problem & will be mindful of Ubuntu's policy (& respect it). I will learn more of Ubuntu & how to deploy it properly over coming months. Thanks again.

CHeers

---

### Post by iaculallad on 2008-08-02
That's your option as a Linux user, to open the root account if you wanted it to and disregard the policy with regard to setting Root password. 
It's you're computer - It's you're choice. But just be sure to set a STRONG enigmatic password for that account.

---

### Post by Dreamerman on 2008-08-04
> **iaculallad said:**
> That's your option as a Linux user, to open the root account if you wanted it to and disregard the policy with regard to setting Root password. 
It's you're computer - It's you're choice. But just be sure to set a STRONG enigmatic password for that account.

Thanks again. I am new to Linux & tend to follow every reasonable help offered. Linux is so different to Win in terms of choices. I love it & aim to be a full convert (ie XPless) soon.

Cheers again.

---

### Post by p_quarles on 2008-08-04
> **iaculallad said:**
>  But just be sure to set a STRONG enigmatic password for that account.
That goes for *any* account that has access to root privileges.

---

