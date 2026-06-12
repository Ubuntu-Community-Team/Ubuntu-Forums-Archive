---
title: "User groups"
date: 2008-09-08
forum: General Help
---

### Post by Ugluk on 2008-09-08
[User management]
Is there a way to add one group to another? Provided GUI U&G applet seems not to have this possibility.

---

### Post by p_quarles on 2008-09-08
Hmm. I can't think of a situation in which you'd want to do that. Can you say a bit about what you're trying to accomplish? There may be a more elegant solution than the one you are looking for.

---

### Post by iaculallad on 2008-09-08
Do you mean creating a sub-group within a group? I think that will not be possible in any given circumstance. And if by chance that could be possible, it would still inherit the same permissions that it's parent group has. The main reason we create group is to control the permissions we give to users.

---

### Post by Ugluk on 2008-09-08
I need to mimic following NTFS rights:

FooGroup    Read (RX)
BarGroup    Change (RWXD)
AdminGroup  Special (PO) // permission/owner change

Only adminGroup should be able to change permissions for given file but not to use file itself.

---

