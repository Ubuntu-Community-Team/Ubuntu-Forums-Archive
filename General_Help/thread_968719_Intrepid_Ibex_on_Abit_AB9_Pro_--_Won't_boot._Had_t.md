---
title: "Intrepid Ibex on Abit AB9 Pro -- Won't boot. Had to go back to Vista."
date: 2008-11-02
forum: General Help
---

### Post by quoderat on 2008-11-02
I've been running Ubuntu on this particular box since Gutsy Gibbon, so I know all my hardware is compatible.

When I have anything plugged into the Silicon Image controller, Itrepid Ibex won't boot. It drops me to a Busybox shell after complaining about some UID of a hard drive not being found.

This occurs even if I remove all drives from the Silicon Image controller during install and only put them back on the controller later. And it occurs if I install with any drives on the SI controller.

The odd things is, I am not actually ever booting off the SI controller, and it worked flawlessly in Hardy Heron with exactly the same setup.

I do need to use that controller. I have six hard drives, one of with is an eSata, and can only use that controller. 

Now I'm forced back to Vista, which is a tragedy. Ideas?

---

### Post by quoderat on 2008-11-03
I finally managed to make it sort of work -- but on installing, it erased two of my hard drives (deleted the partition tables).

Highly recommend against installing on an Abit AB9 Pro. It will funk your shizzle up.

---

