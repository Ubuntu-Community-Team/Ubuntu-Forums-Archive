---
title: "How can I upgrade to UBUNTU 8.10?"
date: 2008-11-17
forum: General Help
---

### Post by volaer on 2008-11-17
What command should I type to upgrade to ubuntu 8.10? CUrrently, I am using 8.04.1 hardy.
Please help.

---

### Post by scouser73 on 2008-11-17
Hi, click **System, Administration, Software Sources**, click the **Updates** tab and make sure that the 4 boxes are checked under the **Ubuntu Updates** section. Next make sure that the **Check For Updates** box in **Automatic Updates** section is ticked and make sure that the drop-down menu is set to **Daily**. Then select the **Release Upgrade** drop-down menu and choose **Normal Releases**. 

Once you have done that go to **System, Administration, Update Manager** and you will see the options for upgrading to 8.10 (Intrepid Ibex)

---

### Post by philinux on 2008-11-17
> **scouser73 said:**
> Hi, click **System, Administration, Software Sources**, click the **Updates** tab and make sure that the 4 boxes are checked under the **Ubuntu Updates** section. Next make sure that the **Check For Updates** box in **Automatic Updates** section is ticked and make sure that the drop-down menu is set to **Daily**. Then select the **Release Upgrade** drop-down menu and choose **Normal Releases**. 

Once you have done that go to **System, Administration, Update Manager** and you will see the options for upgrading to 8.10 (Intrepid Ibex)

**Do not tick** the proposed updates box under the updates tab, especially if this is your main machine.
[https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security]("https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security")
-**Proposed** is the testing area for -updates. A number of people must give positive feedback on these packages before they are allowed into -updates. This repository is recommend to ONLY interested in helping to test updates and provide feedback. Since they are in effect testing updates, there is a higher chance of defective updates in this repository.

---

