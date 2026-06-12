---
title: "Blank Screen on start-up"
date: 2008-09-30
forum: General Help
---

### Post by fknyeah on 2008-09-30
Please help. I'm a novice with no clue about what to do.

I don't remember exactly what I did, but all I did was change some settings in compiz. After restarting my computer goes through normal procedure until the sign in screen, at which point, my screen is completely blank, BUT I can still log in by typing my name and password. It is still blank after that though.  It is not so much blank as it is a gradient from a peachish color to black, not that the color really matters.

I don't know how to fix it and I was hoping I could fix this without having to lose everything I've done to the system already.  I figure I could either disable or uninstall compiz, but seeing as I don't know how to go about doing that while not being able see what I am doing.

I have a Dell Vostro 1500, if that helps.  If there is any more information that would be needed to help solve this problem them I will do my best but I do need to get it in working order again as soon as possible.

Thanks
SFK

---

### Post by MrFSL on 2008-09-30
When you boot you can try dropping down to a terminal by pressing Ctrl + Alt + F1.

From the terminal you can try to replace compiz with metacity by typing:
> metacity --replace

If not you can remove compiz using sudo apt-get remove <name of program>

Good luck.

---

