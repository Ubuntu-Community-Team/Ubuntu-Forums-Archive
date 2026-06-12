---
title: "how frustrating......"
date: 2005-11-15
forum: General Help
---

### Post by jabeez on 2005-11-15
After setting up one computer with Breezy I liked it so much (after hours of forum browsing:) ) that I decided to get another hard drive and install it on my second machine. This went much easier until I tried to network to my other Breezy box. I assumed this would be easy since the original Breezy install saw my windows computer and shares right out of the box, but alas, it is actually harder. When I go to places>network it sees the computer but when I try to access it, it asks for username and password. I have gone through a couple of guides trying to get it working but I've just ended up with places>network seeing more users that I can't access. So seriously, is connecting an Ubuntu box to another Ubuntu box really HARDER than connecting to a Windows box from an Ubuntu box???? This is dumbfounding, not meaning to rant but sometimes......ARGHHH! Any ideas?

---

### Post by Synt4x_3rr0r on 2005-11-15
[QUOTE=jabeez]After setting up one computer with Breezy I liked it so much (after hours of forum browsing:) ) that I decided to get another hard drive and install it on my second machine. This went much easier until I tried to network to my other Breezy box. I assumed this would be easy since the original Breezy install saw my windows computer and shares right out of the box, but alas, it is actually harder. When I go to places>network it sees the computer but when I try to access it, it asks for username and password. I have gone through a couple of guides trying to get it working but I've just ended up with places>network seeing more users that I can't access. So seriously, is connecting an Ubuntu box to another Ubuntu box really HARDER than connecting to a Windows box from an Ubuntu box???? This is dumbfounding, not meaning to rant but sometimes......ARGHHH! Any ideas?[/QUOTE]

I also want to know if you can do this in an easy way.
Right now I have Samba installed on both my Ubuntu machines just to see eachother in the network.
It works fine, but don't you install samba only so you're winows machines can see the linux machines?

So you might want to try that as a temporary sollution? :)

---

### Post by soulestream on 2005-11-15
If you are going *nix to *nix NFS is a better way to go.


as far as the need username and password on the samba share you can create one on the server machine with smbpasswd -a user

soule

---

