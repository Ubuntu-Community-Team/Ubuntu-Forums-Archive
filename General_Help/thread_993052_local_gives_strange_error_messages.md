---
title: "local gives strange error messages"
date: 2008-11-25
forum: General Help
---

### Post by hmeredig on 2008-11-25
Hello,
I've a problem with the locales on my ubuntu 8.10 machine.
If I type "locale", I'll get the following error message:

```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE=en-US.utf8
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

I already tried ```
dpkg-reconfigure locales
``` and ```
locale -a

``` also says that the en_US.UTF-8 locales are available.

Any ideas?

---

### Post by plucky on 2008-11-26
Not really sure what is wrong but ```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
[color=red]LC_CTYPE=en-US.utf8[/color]
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

red entry looks wrong.Should be **"en_US.UTF-8"**

My one looks like ```
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

```

Good Luck

---

### Post by uzi09 on 2008-12-18
I'm having a similar problem. It seems to have started when I installed Arabic support.

The locale LANGUAGE keeps reverting back to "ar" after I change it through the console (I think that's just b/c I did a temp fix) and the rest just don't seem to be set.

```
$ sudo locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
ar_AE.utf8
ar_BH.utf8
ar_DZ.utf8
ar_EG.utf8
ar_IN
ar_IQ.utf8
ar_JO.utf8
ar_KW.utf8
ar_LB.utf8
ar_LY.utf8
ar_MA.utf8
ar_OM.utf8
ar_QA.utf8
ar_SA.utf8
ar_SD.utf8
ar_SY.utf8
ar_TN.utf8
ar_YE.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8

```

Here's how my /etc/default/locale looks like:
```
$ cat /etc/default/locale
LANG="en_CA.UTF-8"
LANGUAGE="en_CA:en"
```
This directory doesn't seem to be doing anything since apt-get (aptitude is what i normally use actually) keeps giving this error until I manually set either LANG="en_CA" or LANGUAGE="en_CA". It's kind of funny because it looks like, LANG should be "**en_CA-UTF-8**" and LANGUAGE="**en_CA:en**" :
```

perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "ar",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```

Another note regarding the above error:
As you can see above, I had sent LANG="en" because otherwise apt-get (aptitude actually) was in a combo of Arabic and English (Arabic mostly). After setting LANG to "en", apt-get worked in English, however the above error is displayed.

[B]Goal: Default language should be Canadian English and be able to switch in and out of Arabic as needed (which I can do now)
[/B]

---

### Post by graabein on 2008-12-23
How do I install Norwegian (nb_NO) locale and set it up only for time format? Don't think I have it installed at the moment.

---

