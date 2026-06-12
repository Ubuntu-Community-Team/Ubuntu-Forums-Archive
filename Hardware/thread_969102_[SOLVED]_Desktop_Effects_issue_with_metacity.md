---
title: "[SOLVED] Desktop Effects issue with metacity?"
date: 2008-11-03
forum: Hardware
---

### Post by Silverspell on 2008-11-03
Dear all,

I am a new Ubuntu (and Linux in general) user, so excuse me if i am posting few details, or if i am asking for obvious stuff.

My laptop configuration is:
Acer Aspire 5672AWLMi
ATI Mobility Radeon x1600 256MB

I recently upgraded from 8.04 to 8.10, and while Compiz and the desktop effects where working fine before with the propriety driver from ATI, now whenever i switch them on, i am loosing the upper bar of my windows (the one that includes the title and the minimize/maximize/close buttons). I tried with and without the propriety driver but still nothing. I purged/ reinstalled compiz and my driver, same issue. I have run compiz-check, and it passes the tests with flying colors (everywhere its [OK]).

Any suggestions,feedback will be much appreciated.

Thanks

---

### Post by tuxxy on 2008-11-03
It dissapeared as you may not have been using Emerald but now its not installed

```
sudo apt-get install emerald
```

Once installed run the following command if still not viewable

```
emerald --replace
```

If you wasnt running emerald then the metacity borders should appear if you run

```
metacity --replace
```

---

### Post by Silverspell on 2008-11-03
I was not running emerald, but after installing it it does seem to work now. Thanks a lot for the fast reply and the help.

---

### Post by tuxxy on 2008-11-03
No problem glad its sorted and you have your borders back :)

You can amrk the thread as solved also

---

### Post by Silverspell on 2008-11-03
I am sorry to reopen this, but the problem seems to persist. Even tho in the beginning it started showing the bars, now they dissapeared again (like if they weren't actually working correctly. I purged and reinstalled emerald, same issue.I used the ```
meaticity --replace
``` command also but it didn't fix it. Any more ideas suggestions?

---

### Post by Silverspell on 2008-11-04
Kk solved eventually.

and no i didn't write meaticity, that was a typo:)

---

