---
title: "[SOLVED] The Mozilla Firefox is unstable!"
date: 2008-10-08
forum: General Help
---

### Post by BSG Fan on 2008-10-08
My Mozilla Firefox 3.0.3 pop outs (disappears) after be opened!
Why happen that?? is there a bug?
Help
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by chriskin on 2008-10-08
i am using the same version of mozzila firefox and it seems to have no problem at all, maybe you should try remove it and add it again , have you tried it?

---

### Post by jerome1232 on 2008-10-08
Also launch it from a terminal and see if you can post any errors that pop up.

Applications->Accessories->Terminal

```
firefox
```

---

### Post by BSG Fan on 2008-10-08
How I remove Firefox really?  Deleting it from the Synaptic Package Manager?
But deleting the packages/processes that accompany them will not put in risk my sistem, etc?
Sorry, I am confused.

I already tried to delete it from the "Add/Remove" (in the applications) but it told me to go and delete it in the Synaptic folder.

other question:
How I launch the "terminal" to type the codes?

Thanks in advance!

=)

---

### Post by BSG Fan on 2008-10-08
How I remove Firefox really?  Deleting it from the Synaptic Package Manager?
But deleting the packages/processes that accompany them will not put in risk my sistem, etc?
Sorry, I am confused.

I already tried to delete it from the "Add/Remove" (in the applications) but it told me to go and delete it in the Synaptic folder.

other question:
How I launch the "terminal" to type the codes?

Thanks in advance!

=)

---

### Post by RATM_Owns on 2008-10-08
Applications->Accessories->Terminal

To remove it, type:
```
sudo aptitude remove firefox
```
In the terminal.

---

### Post by ragflan on 2008-10-08
Terminal can be found in Applications -> Accessories -> Terminal


Maybe your Firefox profile is the one giving you problems. Creating a new profile might help. To create a new profile:

1.) Press and hold ALT with F2.
2.) type: firefox -ProfileManager
3.) The profile manager window comes up.
4.) Click the 'Create Profile' button. 
5.) Click Next.
6.) Give it a name if you want or just leave it as it is.
7.) Press Finish. 
8.) You'll be back at the Profile Manager window. Select the new profile you created. Make sure CHECK the box that says 'Don't ask at startup'.


If Firefox launches with no problems, then it's probably your old profile that was having a problem.

---

### Post by Fc1032 on 2008-10-08
I had to remove firefox from synaptic because of a flash problem. 
Heres how I did it,

Open Synaptic,
on the left column, theres lots of options, go to 'world wide web'
find firefox, right click, complete remove.
It suggests to remove other firefox packages too, just remove as well.

THen re-install using add/remove. Firefox 2 is available for download, it might be better if you want to go back a version. If not, download the first firefox that appears from search

Hope that helped!

---

### Post by jerome1232 on 2008-10-08
Except removing and reinstall  generally doesn't get rid of config files unless you mark for complete removal or use the --purge option from the commandline.

---

