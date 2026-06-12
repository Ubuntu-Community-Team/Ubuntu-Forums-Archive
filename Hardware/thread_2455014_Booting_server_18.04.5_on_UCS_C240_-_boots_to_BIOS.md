---
title: "Booting server 18.04.5 on UCS C240 - boots to BIOS"
date: 2020-12-10
forum: Hardware
---

### Post by araczek2 on 2020-12-10
All-

Finally had gotten all 3 of our UCS C240 servers to boot correctly by working with the boot order in UCS Manager. Developers did an apt-get update and an apt-get upgrade. Now I have the same issue all over again on one server. The server will only boot to the BIOS, it's like it does not know where to find the boot partition again. So the question is would updates like these have any affect on the boot of the system? I am not a linux expert but I don't see that this would cause issues, but I guess it could.

Nothing has changed on the server, they all get the same boot policy and all the BIOS boot options are the same. The other 2 servers boot correctly, they have not had the updating performed on them.

...AR

---

### Post by Kirboosy on 2020-12-14
It sounds like your GRUB might of somehow been corrupted. Are you familiar with the process of booting your server from a LiveCD? Once logged into the Cisco IMC you should be able to mount the ISO via KVM or CIMC.  When the server is booting if you push F12 and instruct the system to boot off the Ubuntu 18.04 ISO. From there you should be able to "Rescue a broken system" and reinstall GRUB.

If you haven't done it lately I would highly recommend updating the firmware on the chassis using the Cisco Update ISO. I know there was a recent security bulletin released for older firmware versions.

[https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-CIMC-CIV-pKDBe9x5](https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-CIMC-CIV-pKDBe9x5)

Hope that helps!

---

