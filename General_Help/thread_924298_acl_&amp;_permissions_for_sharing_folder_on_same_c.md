---
title: "acl &amp; permissions for sharing folder on same computer"
date: 2008-09-19
forum: General Help
---

### Post by Offramp on 2008-09-19
Hi all,

I have just reinstalled ubuntu 8.04 and the family are happy to stay with it and ditch windows! Consequently I am trying to set up a "shared" folder on one computer where we can keep our music/photos/videos. My current intention is to mount a partition called shared for this purpose, and all users must have rwx permissions. Some research indicates that sharing a folder across multiple users is a somewhat troublesome thing to do on ubuntu and I have to use acl.  Is this the best way, or as there are only four of us do I just put us all in a media-share group and change permissions for the shared folders that way.

Any help, comments, feedback would be appreciated.

---

### Post by northern lights on 2008-09-19
Create a new user group called something along the lines of "MediaAccess"

Give the group ownership and rwx rights for the Media folder / partition.

Add all family members to the group.

---

