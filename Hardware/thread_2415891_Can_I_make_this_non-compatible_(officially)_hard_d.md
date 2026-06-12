---
title: "Can I make this non-compatible (officially) hard drive work?"
date: 2019-04-02
forum: Hardware
---

### Post by aomr on 2019-04-02
I use Ubuntu 18.04. Here it says Linux is not supported for the WD Passport Wireless Pro hard drive (or more specifically, only Windows/Mac is mentioned): [https://www.wd.com/products/portable-storage/my-passport-wireless-pro.html](https://www.wd.com/products/portable-storage/my-passport-wireless-pro.html)

On this page someone recommended preparing for a slightly different (non-wireless pro) passport hd by installing an ExFAT library: [https://askubuntu.com/questions/790837/unable-to-mount-my-wd-my-passport-1-tb-in-ubuntu-16-04](https://askubuntu.com/questions/790837/unable-to-mount-my-wd-my-passport-1-tb-in-ubuntu-16-04)

On this thread someone also mentioned using Rsync for something: [https://community.wd.com/t/how-to-use-wd-my-passport-with-ubuntu-linux/9115](https://community.wd.com/t/how-to-use-wd-my-passport-with-ubuntu-linux/9115)


These other drives also do not appear to have linux drivers. Yet I think the posters might have gotten them to work.

Is it possible? What do i need to do or check for? Thanks for any pointers

---

### Post by TheFu on 2019-04-02
Cheap NAS devices usually have lots of security problems.  WD variants have had their share over the years which allowed anything on the storge to be access by anyone knowledgeable over the internet.  Be very careful. The "My Cloud" has been part of the issues.  Be very careful, please.

[https://github.com/ksylvan/MyPassportWirelessHacks](https://github.com/ksylvan/MyPassportWirelessHacks) might be for a different device, but they enabled ssh, so you should be able to use **sshfs**.

The askubuntu link above is for a completely different device.

Directly connected storage devices from WD don't need special drivers, unless they use encryption inside the disk assembly. Yours is a network storage device, which provides a proprietary interface using Windows and Mac software.  They didn't make the software for Linux.  If there are any other standard network protocols that the device supports, there might be help.  

ssh is one, but only you can check the web interface and see if that can be enabled.  

Other common network storage protocols are NFS, CIFS, Samba/SMB or plain FTP.  Never use plain FTP over the internet.  From my quick reading of WD's how-to, they only support anonymous FTP access.  That is available to anyone on the network access - that's delete as well as copy. 
[https://support.wdc.com/knowledgebase/answer.aspx?ID=20556&lang=en](https://support.wdc.com/knowledgebase/answer.aspx?ID=20556&lang=en) has steps to enable plain FTP with it.
 Almost any Linux file manager can access plain FTP locations -   in the URL, put [ftp://x.x.x.x/public](ftp://x.x.x.x/public)    where x.x.x.x is the IP address of the network storage thingy.  You probably want to change the NAS IP address from 192.168.60.1 to something on your network.

---

