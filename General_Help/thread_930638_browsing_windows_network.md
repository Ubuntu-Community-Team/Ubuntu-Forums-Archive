---
title: "browsing windows network"
date: 2008-09-26
forum: General Help
---

### Post by hirohitosan on 2008-09-26
Hi there.
I'm conected in a win network with my Ubuntu and I don't know how to browse the network.
I have samba client and when I try Places>Network -> Windows Network -> WORKGROUP I can see only my computer, no WinXP computers. On Win computers I installed TCP/IP and IPX protocols.
Have any ideea how to see the Win computers?

Thanks

---

### Post by Sycron on 2008-09-26
If you knwo the windows computer ip try ```
nautilus //ip_of_the_comp
```

---

### Post by hirohitosan on 2008-09-26
I don't know the IP just the name. In my office the computers uses DHCP.

---

### Post by Sycron on 2008-09-26
```
nautlus //name_of_the_comp
```

---

### Post by hirohitosan on 2008-09-26
NO. It doesn't work. The win computers can see each others but I cannot see them :(

---

### Post by sparky-steve on 2008-09-26
Its been a while since I did it, but have you checked that you've set your WORKGROUP name in smb.conf (/etc/samba/smb.conf)

in [global], look for/change "workgroup = <name of workgroup>"

or perhaps you want to do:

#smbclient -W <name of workgroup>

Sorry, been a while; hope its of some help.
SS

---

### Post by hirohitosan on 2008-09-26
> **sparky-steve said:**
> Its been a while since I did it, but have you checked that you've set your WORKGROUP name in smb.conf (/etc/samba/smb.conf)

in [global], look for/change "workgroup = <name of workgroup>"

The WORKGROUP is the same with all win computers but still cannot see win computers and they cannot see me ...

---

### Post by gimmejimmy on 2008-09-26
On the XP machines you can type ipconfig /all at a command prompt to get the IP address.

---

### Post by aloshbennett on 2008-09-26
Not sure why you are not able to see the machines in the workgroup. If you know the name, and want to connect, that can be done by 'smb://other-machine-name' from the Run Application prompt (Alt F2)

---

