---
title: "[SOLVED] Website access from other machines"
date: 2008-11-17
forum: General Help
---

### Post by twindragon on 2008-11-17
Hello, 

This may turn out to be a dumb question but it is driving me nuts so I need to ask. 

I have setup a VPC with Xubuntu on it and I installed Apache2/PHP/CGI/GLPI. I have set up the GLPI locally and followed all of the instructions to a T. 

I am able to work on the site if I connect from firefox locally at [http://localhost/glpi](http://localhost/glpi) and for that matter I am able to hit the default "It Works!" if I just go to [http://localhost](http://localhost). 

When I go to the host machine(XP) and type in [http://IP](http://IP) address/glpi (where IP address is that of the Xubuntu guest) I get nothing, and I cannot even see the default "It Works" page. I am able to ping the Xubuntu and I configured the firewall to allow port 80, heck I even tried disabling the fw to no avail.

What did I forget to add to do?

Thanks,

Tom

Forgot to mention it is XUbuntu Hardy that I am working on.

---

### Post by dcstar on 2008-11-18
> **twindragon said:**
> 
........
When I go to the host machine(XP) and type in [http://IP](http://IP) address/glpi (where IP address is that of the Xubuntu guest) I get nothing, and I cannot even see the default "It Works" page. I am able to ping the Xubuntu and I configured the firewall to allow port 80, heck I even tried disabling the fw to no avail.

What did I forget to add to do?
........

There may be an Apache setting that only allows access to your localhost IP address.

You should check the Apache logs to see if connection attempts are getting through.

---

### Post by twindragon on 2008-11-24
Thanks for the response, I never figured it out, just deleted the VPC and restarted from the base install and all worked perfectly second time around.

Cheers,

---

