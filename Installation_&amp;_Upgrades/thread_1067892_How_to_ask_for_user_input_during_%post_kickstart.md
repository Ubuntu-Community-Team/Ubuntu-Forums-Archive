---
title: "How to ask for user input during %post kickstart"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Jorn.jambers on 2009-02-12
Dear,

I am trying to ask for user input during the %post section of a kickstart. The whole kickstart works fine except he doesn't ask for anything I requested(script below). He keeps waiting(hangs on Finishing the installation - Running kickseed...) When I switch terminal to tty3 I can see my first question but can't fill it in. And due to this the setup won't proceed. Is there a way to resolve this?

Thx in advance 

```

%post
echo "################################"
echo "# Running Post Configuration   #"
echo "################################"
echo -n "Give FQDN node: "
read hostn
hostname $hostn
echo $hostn > /etc/hostname

echo -n "IP-addres of Puppet-master: "
read puppetmip
echo -n "FQDN of Puppet-master: "
read puppetmfqdn

echo "$puppetmip	$puppetmfqdn" >> /etc/hosts
puppetd --server $puppetmfqdn --verbose --waitforcert 60 --test

```

---

### Post by Jorn.jambers on 2009-02-12
This is the workaround. If you sent the questions you want to ask to tty6 you can fill them in. In tty1 to tty4 runs bussybox so you won't be able to get the user input. When you press enter in tty1 to tty4 he will activate the console and will not understand the input.

```

%post
exec < /dev/tty6 > /dev/tty6
chvt 6
clear
echo "################################"
echo "# Running Post Configuration   #"
echo "################################"

###Go back to tty1##
exec < /dev/tty1 > /dev/tty1
chvt 1


```

---

