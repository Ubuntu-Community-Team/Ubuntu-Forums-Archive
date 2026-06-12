---
title: "Is virtualization/hypervisor a solution for my needs?"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by salmanjamali on 2009-06-02
Hi!
 
Foa, sorry for the vague subject, i tried to grab attention ](*,) I recently assembled my desktop machine and installed ubuntu 9.04. I plan to use it primarily (switching from windows). I want the machine to serve the following purposes:
[LIST=1]
[*]Subversion for all my java, perl, and php code;
[*]A webserver for my blogs;
[*]Using the 4 cores (Phenom 2 x4 940) for my research related cpu intensive processes (sometimes);
[*]Host a file server (to share media with family);
[*]Do programming,
[*]Install, test, and uninstall different middleware projects (jboss etc.);
[/LIST]I might be asking too much, but I won't be doing this all at the same time. Now, I see that I should think in terms of virtualization (hypervisor perhaps). Should I be using type 1 or type 2 hypervisor? What would be an optimal virtualization configuration for my needs?
 
**I am too good at messing up the configurations and installations. So, I want to make sure that all of my 6 purposes should remain isolated. I also want the webserver to run flawlessly, so should it be inside a VM or installed on the Host itself?**
 
Please elaborate your suggestions, thanks a lot!

---

### Post by MichaelSammels on 2009-06-02
I think you could possibly install say Ubuntu Server Edition, and then install Xen on top of then. Then install Ubuntu Desktop Edition into Xen.

---

### Post by salmanjamali on 2009-06-02
> **MichaelSammels said:**
> I think you could possibly install say Ubuntu Server Edition, and then install Xen on top of then. Then install Ubuntu Desktop Edition into Xen.
 
What about MonkeyNet's reply here: [http://ubuntuforums.org/archive/index.php/t-225546.html](http://ubuntuforums.org/archive/index.php/t-225546.html)
 
I would be requiring gnome or kde, and I'll do coding too. How about u-desktop-ed as host and Xen on top of it; then, 1 u-server-ed in one of the vms?

---

