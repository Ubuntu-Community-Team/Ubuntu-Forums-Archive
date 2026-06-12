---
title: "SMB/CIFS file sharing to windows"
date: 2005-11-07
forum: General Help
---

### Post by dubuntu on 2005-11-07
Can anyone point me to the best (i.e. easiest and quickest) place to get info on how to setup samba to talk to a windows xp machine on my network?

thanks

---

### Post by Maverick911 on 2005-11-07
I'm having problems accessing shared folders on my WinXP computer from my laptop running Breezy 5.10. I've finally got the wireless working with ndiswrapper, I can access the internet, but when I browse "Computer there is no icon for "network". I've set the IP addresses domain name properly. WIKI page on setting up Samba says to enter these settings under the general tab for my network interface.

    Host Settings
      Hostname:       <yourcomputer>
      Domain name:    <yourdomain>

    Windows Networking
      Tick Enable windows networking
      Description:       <whateveryouwant>
      Domain/Workgroup:  <yourdomainorworkgroup>

   If you want tick WINS server  <thenameoripaddressofyourwinsserver>

The only settings I have under the general tab are Host Settings. What am I missing here?

---

