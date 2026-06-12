---
title: "virtual box hdd"
date: 2009-04-30
forum: Hardware
---

### Post by sridarshan on 2009-04-30
i installed ubuntu jaunty jackalope in my windows vista using virtual box,i created a virtual hard disk of 8 gb,and installed it.

but the thing is i cant browse any other drives other than my home drive of 8 gb,is there any way i can browse my rest of the drives as well to enjoy jaunty to its fullest:(

---

### Post by Barry Carroll on 2009-04-30
That's the way virtualisation works really.  As far as the VM is aware you only have that 8GB disk.  What you can do however is to connect to your windows shares by adding them through "Places" and then "Connect to Server"

---

### Post by sridarshan on 2009-04-30
> **Barry Carroll said:**
> That's the way virtualisation works really.  As far as the VM is aware you only have that 8GB disk.  What you can do however is to connect to your windows shares by adding them through "Places" and then "Connect to Server"


how do i add my window shares to places??please help:)

---

### Post by Barry Carroll on 2009-04-30
Firstly you'll need to set up some shares in Vista.  You can usually such a thing by right-clicking on a folder and looking for a section or tab called 'Sharing' and enable it there.

In ubuntu there's a 'Places' menu across the top left of the screen.  Click on that and go to 'Connect to Server'.  Change the service type to 'Windows Share' and enter in the details.

The important ones are: 

'Server': put the **windows **IP address of your pc here, you can find this out in windows by doing a ```
ipconfig 
```con the command line and looking for the IP address related to your network card.

'Share': this will be the name of the share in windows, and you can edit this in windows when you are sharing.  It'll be called 'shared as' or something similar

'User name':  this is the username that you log into windows with

I'm on a domain so I had to put that in the domain textbox but if you're just on a home network you can leave that out.  If it doesn't work then try your windows workgroup name.

That should work fine, it works well for me anyway so I hope it does for you too!

---

