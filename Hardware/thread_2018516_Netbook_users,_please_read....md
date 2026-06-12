---
title: "Netbook users, please read..."
date: 2012-07-06
forum: Hardware
---

### Post by Marcelo Ruiz on 2012-07-06
Hi All,

I've been having annoying problems with way to many programs in Ubuntu when I use them in my netbook. The reason: too many dialogs/windows are designed with larger height than the screen, making their content inaccessible.
I filled a bug in lauchpad about that. Please feel free to post your comments there if you also experience this issue.
I feel this is a serious usability problem that needs to be addressed as soon as possible.
Thanks!

[https://bugs.launchpad.net/ubuntu/+bug/1021790]("https://bugs.launchpad.net/ubuntu/+bug/1021790")

---

### Post by RaumTrug on 2012-07-06
Normally, there's ways to drag windows around clicking anywhere on them. In xubuntu, for example, you can hold the "alt" key, and move the window by dragging with mouse/touchpad.

---

### Post by Marcelo Ruiz on 2012-07-06
Well, I tried pretty much everything in Unity with no luck. My last frustration was trying to create an e-mail account with Evolution, the buttons to move forward and cancel were totally hidden, and there was no way to drag nor resize the dialog. I still believe this is a major problem...

---

### Post by bohemian9485 on 2012-07-07
I'm also using Lenovo S10-3 Ideapad netbook and I can understand your problem. Under Unity you cannot drag your windows beyond the top panel and I found it quite annoying. That's why I'm using either gnome classic or glx-dock desktop, then I can drag my windows wherever I want.

---

### Post by PaulW2U on 2012-07-07
> **Marcelo Ruiz said:**
> I've been having annoying problems with way to many programs in Ubuntu when I use them in my netbook. The reason: too many dialogs/windows are designed with larger height than the screen, making their content inaccessible.
I filled a bug in lauchpad about that. Please feel free to post your comments there if you also experience this issue.
I feel this is a serious usability problem that needs to be addressed as soon as possible.
Thanks!

[https://bugs.launchpad.net/ubuntu/+bug/1021790]("https://bugs.launchpad.net/ubuntu/+bug/1021790")

I see that you've filed the bug against Ubuntu but if the dialog boxes are too big for your netbook screen I'm not sure it's Ubuntu's fault. I would have thought you would need to file bugs against each application or suite of applications for which this problem exists.

I have experienced this issue and the way I get around it if I am using the top two workspaces in Unity is to move any large dialog boxes down a little, if that is possible and then display the workspace below the one I am using. That workspace will most likely be displaying any hidden buttons which can then be clicked. You can then move back to your original workspace and continue with what you were doing.

A long press of the Super key should display the Unity short cut menu. But it won't on a netbook due to the restricted size of the most common screens. The developers say this bug will not be fixed and I suspect that the developers of other applications also won't want to resize the larger program windows and dialog boxes just to suit netbook users.

---

### Post by Marcelo Ruiz on 2012-07-07
Hi Paul,

I do think it's Ubuntu's fault not to give a clean solution to this problem, because a lot of the applications that ship with it have that problem.
Ideally I would like all windows and dialogs be capable of being resized (even the fixed sized ones). I know that will intuitively go against their design, but if you have just one screen, you should be able to see the content in that screen.
How would I solve this? Just forcing a scroll pane with hidden scroll bars as the first component and adding all the content to it. If the window/dialog size is bigger than the screen (you could also detect if the user has an external monitor connected and take that into consideration) the OS should force them to fix in the screen, revealing the scroll bars that will allow users to do whatever they need to accomplish their task. Under other circumstances, the dialogs and windows will behave as they do now.
I don't think this will be a huge fix to implement and I believe this will solve all screen problems with one shot.

---

