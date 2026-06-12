---
title: "Bug: root's Desktop instead of user's Desktop"
date: 2005-11-03
forum: General Help
---

### Post by Seb71 on 2005-11-03
After I used nautilius as root (with "Run as different user"), my Desktop was replaced with root's Desktop.

Instead of:
/home/user_name/Desktop
now it is:
/root/Desktop.

For instance if I right click on the desktop and select "Create Folder", the new folder is created in /root/Desktop and not in /home/user_name/Desktop. Also if I want to show the Computer icon on desktop, I have to enable this for root and not for the regular user.

I used nautilius as root because I wanted to make a new folder in /home.

I am logged in as a regular user.

I did not enabled the root account (for login as root).

How can I correct this bug?

---

### Post by SavageBeginner on 2005-11-03
What exactly are you trying to do?

---

### Post by Seb71 on 2005-11-03
[QUOTE=SavageBeginner]What exactly are you trying to do?[/QUOTE]

I want to restore the correct desktop (without reinstalling Ubuntu).

---

### Post by SavageBeginner on 2005-11-03
What do you mean by "correct desktop"?  What's on your desktop now?

---

### Post by Seb71 on 2005-11-03
I am not talking about the desktop background.

I am talking about the Desktop **folder** (the folder which is displayed on the desktop). 

For instance, you can choose one of the following two folders to be displayed on your desktop (as your desktop):

/home/user_name/Desktop - This is the default setting
/home/user_name - This in User's Home Folder


As I explained in my first post, in my case this folder changed to:

/root/Desktop

This would be correct if I was logged in as root, but I am logged in as "user_name" user (I am logged in as a regular user).

---

### Post by felix_stegerman on 2005-11-03
You should have your own desktop back after you log out and back in.
To be able to use nautilus as root without it taking over your desktop, use
# sudo nautilus --no-desktop

Felix

---

### Post by Seb71 on 2005-11-03
I allready tried with log out and then log back in. Also I restarted the computer. Neighter solved the problem.

Now I made a Shut Down and after that my Desktop is again the correct one.

Problem solved. Thanks.

---

