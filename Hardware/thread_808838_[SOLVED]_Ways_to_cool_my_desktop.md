---
title: "[SOLVED] Ways to cool my desktop"
date: 2008-05-26
forum: Hardware
---

### Post by halberd25 on 2008-05-26
This is a general question, but maybe you can help anyway.  I built my pc from scratch, and it's housed in a micro atx case.  I have an AMD Phenom 9500 processor that runs very quiet and cool, but the 300w power supply that came with the case runs really noisy when it gets hot.  How are some ways I can cool down my computer?  I don't want to replace the power supply because I read that the life expectancy of micro atx power supplies is low.

---

### Post by tamoneya on 2008-05-26
replace CPU cooler
Try to reoganize wires to improve airflow
add a new case fan to improve airflow

---

### Post by Twintop on 2008-05-28
Like tamoneya said, try to organize your wires for better air flow and having case fans never hurts. However, adding more components (like fans) is just going to drain more power, which will cause the PSU to pump out more power, which will increase heat...

If you can, get powernowd to work with the Phenom with the k8 drivers to get your processor running at a lower frequency as much as possible. That will help some with reducing power consumption.

I know that you don't want to replace it, but the biggest problem might be the power supply itself. That 300W PSU is probably running at near peak output all the time with your Phenom, so it might make more sense to buy a better/more powerful PSU.

---

### Post by tamoneya on 2008-05-28
its not so much a matter of PSU power but of efficiency.  Say your PSU is running at 85% efficiency(This would be a new nice CPU) and the computer is drawing 300 Watts.  The total amount of power that the PSU is drawing out of the wall would be 300/.85 = 350ish watts.  The difference in the wattages (350W - 300 W) is the power that gets disappated as heat.  In this case 50 W of heat.  Now you cant really change the amount of power that the computer draws  (you can a little with powernowd) so it is best to increase the efficiency so that the power disappated as heat is minimized.  Also note that the effiencies that are listed on most power supplies are the peak efficiency and this often occurs near the top of its power range.  So a 300W power supply will probably reach peak efficiency around 280W or so.  It doesnt  make sense to buy up for a 700 W powersupply because for your computer running around 300W will be not at the rated 80-85% efficiency because it is well below peak.

---

