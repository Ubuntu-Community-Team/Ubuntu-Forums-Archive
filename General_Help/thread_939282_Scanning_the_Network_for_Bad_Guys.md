---
title: "Scanning the Network for Bad Guys"
date: 2008-10-05
forum: General Help
---

### Post by CrusaderAD on 2008-10-05
Is there anyway to scan your network to see if anyone other than your machines are logged into the wireless network? Perhaps a program to show you all the leases on your router? How about the best way to go about locking down your network? Which security feature is the best?

---

### Post by ghantoos on 2008-10-05
You could try nmap to see what IPs are reachable.

Say your your network is a 192.168.1.0/24:
```

nmap -sP 192.168.1.0/24

```Hope this helps,

Cheers,

---

### Post by CrusaderAD on 2008-10-05
Thanks for the reply. What does /24 signify?

---

### Post by ghantoos on 2008-10-05
24 is the mask length of your network. It means that your network is set to have maximum 254 hosts.

ie. from 192.168.1.1 -> 192.168.1.254

Here a nice link:
[http://articles.techrepublic.com.com/5100-10878_11-6089187.html](http://articles.techrepublic.com.com/5100-10878_11-6089187.html)
(refer to Figure C)

Cheers,

---

### Post by CrusaderAD on 2008-10-05
Thanks! This may sound a little unethical... but do you know of any links or articals referring to hacking network machines? My only reason for asking is because I am really paranoid about my wireless and would like to know how it works from the other side of things.

---

### Post by ghantoos on 2008-10-05
You could take a look here: [http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php)

Cheers,

---

