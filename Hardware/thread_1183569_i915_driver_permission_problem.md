---
title: "i915 driver permission problem?"
date: 2009-06-10
forum: Hardware
---

### Post by Ferrat on 2009-06-10
Everytime I run something 3D I get 
```
get fences failed: -1
param: 6, val: 0
drm_i915_getparam: -22

```

And apparently this is purely a permission it seems from what I can find on the matter, not many take it up directly but found a thread on an old Unreal forum where ppl got rid of it when starting with sudo. 

And I have found the Trouble shooting Intel on the wiki and they address a permission problem, how ever from what I can see 

```
iceglider@iceglider-min:~$ ls -l /dev/dri/card0
crw-rw----+ 1 root video 226, 0 2009-06-10 13:26 /dev/dri/card0

```

```
iceglider@iceglider:~$ getfacl /dev/dri/card0
getfacl: Removing leading '/' from absolute path names
# file: dev/dri/card0
# owner: root
# group: video
user::rw-
**[COLOR="Red"]user:iceglider:rw-[/COLOR]**
group::rw-
mask::rw-
other::---
```
this red part indicates that the access-list is working as it should and there should be no permission problem?

Before I just got the two first lines until I updated and now I get those three.

Does anyone know what permissions isn't correctly set or have a fix to it?

ps.  should add that the 3D apps work but want to fix this since it might affect performance etc

EDIT: 
Sudo doesn't remove the output so there might not be a permissions problem, but tried it with OpenArena and gained ~5-10FPS using sudo?(and when playing with ~15-20 FPS that's great)

---

