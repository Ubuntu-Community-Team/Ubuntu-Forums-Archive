---
title: "Permission question regarding Samba and a second local hard drive."
date: 2008-11-29
forum: General Help
---

### Post by Roasted on 2008-11-29
I have a Samba setup with a spare 250gb SATA drive I have in my computer. I personally don't use it for my own sake. I just have Samba routed through that drive so my two brothers and mom can back stuff up to it.

They each have designated password protected folders. And they each run XP Pro. Each one of them also has SyncToy, which synchronizes everything in their my documents folders to \\myserver\theirshare. Works great.

But I just ran into a little qwirk. My brother had an error with SyncToy, so I decided to reinstall it. I had the msi installer on my Ubuntu computer. So, I just dropped it in his share.

Then on his computer I went to start - run - \\jason-intrepid\tyler (his share) to grab the msi installer package. I copied it, and when I went to paste it it said write protected, cannot continue.

I went back and sure enough when I right click on that installer file and look at the permissions, "others" has no permissions. So I check read and write, go back to his computer, and bam. I can do what I want with it.

My question is, and this may not be Samba related now that I think about it, but is it just a security feature that all files copied to another location retain read access only? I mean, even though Samba is in the picture here, all I really did was copy/paste a file from my hard drive to my secondary hard drive. My secondary hard drive is the one routed through Samba.

Is it just a security feature?
Can it be changed so I can paste items there all the time without changing permissions?
If I select multiple files (or even use select all), if I right click on all of the selected files at once and go to the permissions tab, can I change ALL of their permissions?

Note - I'm familiar with chmod, and I assume with the permissions I'm speaking about above the tag for it would be chmod 777. But I'm just trying to see alternatives to CLI, as much as I like CLI. I just like to find other ways of doing things.

Any input, folks?

---

