---
title: "complete system hangs, seem to be nvidia driver related?"
date: 2008-10-29
forum: General Help
---

### Post by kmolnar on 2008-10-29
I have two completely different applications here - One is Linden Research's Second Life viewer, the other is Blender. Both use OpenGL and, thus, hardware acceleration. That's about all they have in common, aside from this bug...

In Blender, when doing pretty much any operation on object vertices, I get a hang of a few seconds - a complete system hang. X stops updating, gnome-system-manager stops updating (records a single infinitessimal spike of100$ usage though), all programs stall. Very strange. That immediately makes me think it's a driver thing.

In Second Life, the same thing happens, but under conditions I can't quite nail down. My thought is it might have something to do with vertex buffer objects or some craziness like that. I can't quite profile it to a place that explains where the time is being wasted.

So I have the exact same bug in two apps that share basically nothing except some common libraries like OpenGL... I *think* it's the nvidia driver, because the few other people I have seen who have this issue tend to have NVIDIA cards also.

I'm using Ubuntu 8.04
GNOME
Compiz (tried without also, same behavior)
  Note: Compiz never triggers this by itself. It seems like the problem happens specifically with 3D-intensive applications, likely due to some poorly supported feature they're both using

I wish I had better information on this, but I'm not even sure how to debug it.

Anyone else have these issues and/or can try out the mentioned applications if they have the same driver? I'd like to at least eliminate some variables from this madness. =)

Thanks!
- Katie

---

