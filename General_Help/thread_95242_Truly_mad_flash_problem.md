---
title: "Truly mad flash problem"
date: 2005-11-26
forum: General Help
---

### Post by lerrup on 2005-11-26
Flash was never a problem for me in Warty, Hoary or Breezy until I installed f-spot.  After this firefox would crash whenever it came across flash.  epiphany, being a gecko browser also crashed.  Konqueror, being different, didn't crash but only showed a grey rectangle where the animation should have been.  Right clicking on the grey rectangle brought up the flash-player menu which allows you to adjust quality, etc.  None of this made any difference.

I reluctantly took off f-spot and anything with that came up when I searched using the word "mono" in synaptic.  Flash was still stuffed.

I reinstalled it, changed flash packages and installed the package from the flash website. No change.  I followed arnieboys tips, nothing.  I took off firefox and all its directories and anything with the word mozilla in it in /usr/lib. I then did a clean install. No difference.

This is starting to hurt.

---

### Post by Janherbergh on 2005-11-26
Oh, well, first of all tell you i'm not english (i'm spanish) so probaly you will find my english being terrible (sorry)

Well, i had the same problem, even try to intall some independent flash-players, but they didnt' work correctly, and was frustrating! 

Then i tried to upgrade the flash plugin, by download it from firefox plugins page and i installed it via copy-paste in the home/user/.mozilla/plugins and worked for me... So maybe this will work for you...

Luck!

---

### Post by jmooney on 2005-11-26
This wound up working for me as well:

sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc

Then comment out FIREFOX_DSP="auto" and add the line FIREFOX_DSP="none"

# which /dev/dsp wrapper to use
## FIREFOX_DSP="auto" ## The default setting
##
## This is supposed to fix the problem with Macromedia flash plugin.
FIREFOX_DSP="none"  ## Set by Joseph K. Mooney on 11/25/05
##                  ## Confirmed working on [www.abum.com](www.abum.com)


Of course, your could just change "auto" to "none" but, whenever I modifiy a config file, I like to leave a note to myself explain what I did, when I did it, why I did it, and if it worked.

but suit yourself.

---

### Post by lerrup on 2005-11-27
Thanks for your suggestions.

Flash is however going on not working...

Are there any mono experts who might be able to suggest anything?

---

