---
title: "Purchased 4gb ram from 2gb, increase swap? reinstall ubuntu?"
date: 2008-11-21
forum: Hardware
---

### Post by Capslock118 on 2008-11-21
Hi,

I just purchased a laptop with 2gb of ram. Unfortunatly it has an integrated graphics chip and so shares the ram. I also want xp/vista on a virtual machine.

That said I purchased 2 2gb sticks of ram as my laptop supports 4gb.

Questions:
1. Will I be required to re-install ubuntu once i upgrade the ram?

2. I currently have 4gb of swap. As the rule of thumb goes keep your swap double the size of your ram. my partitions are laid out as follows: 20gb /, 4gb swap, 176 /home.

Since swap is in the middle, will it be possible to increase the swap and decrease the home drive (or /) without destroying data? does a resize move data over where the resize is suppose to take place? Is this safe to do or would it be best to reformat and start fresh?

if I cant resize the swap I will either re-install ubuntu or just forget about it and leave it at 4. I would just like to know my options.


Thanks in advanced for any input.

---

### Post by Bucky Ball on 2008-11-21
1/ Shouldn't need to
2/ With that much RAM, you have no need to increase swap. Two Gb is in fact adequate when you have that much ram (you will barely if ever use it all so minimal spill into the swap, which is not as fast as physical RAM anyway). Check out System->Administrator->System Monitor and boot some of your hungriest apps and check out the stats on the monitor.

---

### Post by Therion on 2008-11-21
1.  No.

2.  That calculation of virtual memory needing to equal 1.5 (or 2.0) * the system's total RAM is archaic.  Forget about it.  The more RAM you have, the less likely you are to need virtual memory.  Add your additional memory sticks and get on with life.  If it was easy to do, I'd tell you to *reduce* your swap partition down to a 1GB or less, just so you could recover the HDD "real-estate" you've lost to it.  As it is, add the memory, and forget about your swap partition.

---

### Post by daveerickson on 2008-11-21
> **Capslock118 said:**
> Hi,

I just purchased a laptop with 2gb of ram. Unfortunatly it has an integrated graphics chip and so shares the ram. I also want xp/vista on a virtual machine.

That said I purchased 2 2gb sticks of ram as my laptop supports 4gb.

Questions:
1. Will I be required to re-install ubuntu once i upgrade the ram?

2. I currently have 4gb of swap. As the rule of thumb goes keep your swap double the size of your ram. my partitions are laid out as follows: 20gb /, 4gb swap, 176 /home.

Since swap is in the middle, will it be possible to increase the swap and decrease the home drive (or /) without destroying data? does a resize move data over where the resize is suppose to take place? Is this safe to do or would it be best to reformat and start fresh?

if I cant resize the swap I will either re-install ubuntu or just forget about it and leave it at 4. I would just like to know my options.


Thanks in advanced for any input.

Here is a link that can give you some information so you can choose what to do. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I would leave you swap alone since you now have a swap partition the same size as your physical ram, which is necessary for a laptop to hibernate.

On laptops I still create a swap partition of 1-1.5x the ram, and no swap partition for desktops since i never hibernate. Then on the desktops I create swap files as needed.

Hope this helps.

---

### Post by Capslock118 on 2008-11-21
Interesting read.

Well, I do not really use hibernation. Perhaps hibernation has improved over the years, but back when i was in tech support windows machines would come to my desk and I would have to re-install windows because it could not get out of hibernation. 

I know this is ubuntu, but the idea still scares me.

That said, yeah since the swap is 4gb I might as well just keep it as is and not worry about resizing.

Thanks for your input folks.

---

### Post by daveerickson on 2008-11-21
> **Capslock118 said:**
> Interesting read.

Well, I do not really use hibernation. Perhaps hibernation has improved over the years, but back when i was in tech support windows machines would come to my desk and I would have to re-install windows because it could not get out of hibernation. 

I know this is ubuntu, but the idea still scares me.

That said, yeah since the swap is 4gb I might as well just keep it as is and not worry about resizing.

Thanks for your input folks.

I have used the hibernate option and have never had to reinstall after. Sometimes on some equipment it doesn't actually hibernate, but never destroyed the whole install. I like Suspend better anyway, that or shutting down. Isn't it great to not have to do daily battle with microsoft crap? :)

---

