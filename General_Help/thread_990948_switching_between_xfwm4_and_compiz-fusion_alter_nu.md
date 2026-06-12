---
title: "switching between xfwm4 and compiz-fusion alter number of workspace"
date: 2008-11-23
forum: General Help
---

### Post by alau4000 on 2008-11-23
Installation: xubuntu 8.10 + compiz-fusion 0.7.8 + kde 4.1.3. Setting up 4 workspaces under xubuntu xfce4. Switching to the Compiz-fusion enviornment with the compiz Fusion Icon. The 4 workspaces remain in the panel under the compiz-fusion (it is hard to see though, because the inactive workspaces have the same color as the panel). Now, switching back to xfce4 (i.e., selecting xfwm4 manager) through the Compiz Fusion Icon, and only one workspace remains in the panel. I can reset the number of workspace to 4 through the Workspace Manager. If I switch it back to the compiz-fusion again, there are 4 workspaces appear back in the panel.

Just wondering if it happens to anyone else? BTW, is there anyway change the workspace-icon (active and inactive) color in the panel? Under the compiz-fusion, I can kick and switch workspace, so I know it is there even though I can't really see it (inactive window workspace icon is white which is the panel color)

---

### Post by j1mc on 2008-11-25
Hi there, 

Compiz on XFCE still isn't fully functional, but [here]("http://forum.compiz-fusion.org/showthread.php?t=9278") is something that I've found to be helpful in this situation.  

Go into Applications > Settings > Compiz Config Manager Settings, then select General Options, and the Desktop Size tab.

On the Desktop Size tab, set the Horizontal Virtual Size to 4, and the other options to 1.  

Click on the back button, close the Compiz Config Manager, close all other applications, log out, and log back in, and it should work.  The pager applet in the lower-right corner won't show that it's flipping from one workspace to another, so it isn't fully fixed, but the cube functionality should be working with all four sides now.

Please let me know if this doesn't work.  Thanks!

---

### Post by murthy on 2012-12-23
Setting <<Compiz Settings Manager -> General Options -> Desktop Size to:
Horizontal Virtual Size - 4
Vertical Virtual Size - 1
Number of Desktops - 1
solves the problem of workspace switcher not showing the running applications properly and other issues with the workspaces switcher in Xubuntu 12.10 + Compiz.

---

### Post by oldos2er on 2012-12-23
Old thread closed, please don't bump old threads.

---

