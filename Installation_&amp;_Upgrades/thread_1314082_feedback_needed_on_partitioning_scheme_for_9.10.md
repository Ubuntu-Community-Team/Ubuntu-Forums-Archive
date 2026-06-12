---
title: "feedback needed on partitioning scheme for 9.10"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by pinknyunyu on 2009-11-04
I'm finally ready to install Karmic Koala, but I wanted the forum's feedback on the partitioning scheme I was planning on using.  I usually just do swap, /, and /home, but I wanted to get fancier this time.  Although I know it's not completely necessary, because I'm just using this as my home computer, I wanted to split / into multiple partitions because my HD is big, and because as I understand it's more secure as well.

I have multiple HDs, but I was going to use the newest, fastest, biggest HD (in comparison to the rest, that is) that I have for Ubuntu, so the rest of what I'm doing to my computer really doesn't matter, except for the fact that I'm splitting my swap across the HDs (and that I plan on only toying around with Linux and BSD).

Everything but the swap is going to be ext3.

My entire Jaunty root installation only used a little over 4.5gb, so I'm allotting a lot more space than I think I'll actually use for Karmic, but I also know that some people allot a lot more space to Ubuntu.

I wanted to do swap, extended root partition, home, and then data, but gparted kept naming the logical partitions out of order, even when I wiped everything and started from the beginning, so I had to stick the logical partitions at the end.

sda1 - swap - 2gb 
sda2 - data - 579gb 
sda3 - /home - 2 gb (just for dotfiles and configuration files...all my documents are going in data so they're easier to share across operating systems)
sda4 - extended
sda5 - /boot - .5gb
sda6 - / (root) - 2gb
sda7 - /usr - 6gb
sda8 - /var - 3gb
sda9 - /tmp - 2gb

Thanks!

---

