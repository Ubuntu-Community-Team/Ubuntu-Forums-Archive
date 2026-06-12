---
title: "Web Filter"
date: 2008-10-19
forum: General Help
---

### Post by jaminthorns on 2008-10-19
Okay, My dad has been getting all over me about how I need a filter for blocking stuff online. He wants wants a setup in which he knows the password and only he can access it from my laptop. I just recently switched from Windows Vista to Ubuntu and I am (or rather he is) looking for an equivalent of Canine Web Protection but for Linux. I've already tried Dansguardian and he said he didn't like it, therefore I need some more suggestions.

Can anyone help me? I don't need installation instructions or anything just the name of a good program. By the way, I'm using Opera 9.60 and Intrepid 8.10 Beta.

---

### Post by p_quarles on 2008-10-20
Well, ultimately web filtering should be done on an entire network, and should be centralized. Putting it on an individual laptop is something that is so easily circumvented as to make it pointless. 

There are several packages available in the Ubuntu repositories that can do proxy filtering. Search for them in Synaptic and try them. Dansguardian is the most popular home solution for this kind of thing, and that's what most people here will be familiar with. 

Again, it would really only make sense to have this running on a separate computer.

---

### Post by Nepherte on 2008-10-20
You could also use another DNS server (openDNS). You can then filter parts of the internet, though it's not 100% perfect.

---

### Post by sethvath on 2008-10-20
I second OpenDNS [http://www.opendns.com/smb/solutions/filtering/](http://www.opendns.com/smb/solutions/filtering/)

Refer your dad to the weblink above, should be easy for him to use.

---

