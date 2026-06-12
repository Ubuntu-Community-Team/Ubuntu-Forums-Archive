---
title: "External unmounts randomly.."
date: 2009-04-29
forum: Hardware
---

### Post by qjmoss on 2009-04-29
I was having problems with 8.10, so i decided to give 9.04 a shot, as far now, I love it, I understand it's still a  little beta.

but this is a problem I was having with 8.10 also.

I have a Western Digital (my book) 1tb external hard drive.


Now, when I'm downloading something, or moving something to my external it will randomly unmount and I get all kinds of errors.

I hope someone else has had this problem and has a solution.

I was thinking maybe it has a power saving option..

bah i don't know, any help would be wonderful

---

### Post by seish on 2009-04-29
Can you paste the error it gives you?

I have a 500g Seagate FreeAgent external with its own power source.  

After being idle and mounted for a few minutes it locked up and became unmountable under any of my  linux PCs. There was a long error message offering a solution, but what I did was:

1) Try to mount it on my dad's Windows XP - it worked.
2) I installed the windows software for the drive and disabled the auto idling(or power saving or something of the sort) feature because apparently the issue was that when the external spins down after being idle for 5 minutes it loses its USB connection for a second and mounts itself under a different id. I updated the firmware also, but I think the problem fixed with the first thing I did since I read that it was a common error.

3) I shut down the external proper under windows and it worked after reboot.


Our externals are different models but I hope this solution works for you too. GL ombre.

---

