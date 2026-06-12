---
title: "No Thesaurus for English (UK) in OpenOffice 3"
date: 2008-11-10
forum: General Help
---

### Post by Pocito on 2008-11-10
Hi,

I've upgraded to OpenOffice 3 in Intrepid.I notice there's no thesaurus available when I set the language in OpenOffice to English (UK). Is there any way to enable a thesaurus for this language setting? I'm sure there must be a way to do this.

Thank you for any help you give.

---

### Post by jason.b.c on 2008-11-10
you want open office to correct the spelling of words like "oi" and "wanker" and "blutty yank"...?

---

### Post by Pocito on 2008-11-10
Thanks for your reply jason.b.c.

No, the spellchecker is working fine. It's the thesaurus function that's missing. Do you have any ideas as to how to get this to work? Any suggestion is welcome.

---

### Post by TeXtonyx on 2008-11-10
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&p=46966](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&p=46966)

[url]http://user.services.openoffice.org/
en/forum/viewtopic.php?f=7&p=46966 [copy and paste into browser as one line]

---

### Post by Pocito on 2008-11-10
Thanks for your reply TeXtonyx.

I've already seen the thread that your post suggests I look at, but unfortunately it didn't solve my problem. Please find below the contents of my /etc/openoffice/dictionary.lst file which I haven't modified at all. As you can see, right down the bottom there is already an entry that reads *THES en GB th_en_US_v2*, so I'm still a little stuck. 

```

## List of All Dictionaries to be Loaded by OpenOffice.org
## ---------------------------------------------------
## Each Entry in the list have the following space delimited fields
##
## Field 1: Entry Type "DICT" - spellchecking dictionary
##                     "HYPH" - hyphenation dictionary
##                     "THES" - thesaurus files
##
## Field 2: Language code from Locale "en" or "de" or "pt" ...
##
## Field 3: Country Code from Locale "US" or "GB" or "PT"
##
## Field 4: Root name of file(s) "en_US" or "hyph_de" or "th_en_US"
##          (do not add extensions to the name)
##
## This file is automatically updated by update-openoffice-dicts script
##

## !!! BEGIN AUTOMATIC SECTION -- DO NOT CHANGE !!!
## !!! ADD YOUR ADDITIONAL ENTRIES BELOW THIS SECTION !!!
DICT en AU en_AU
DICT en GB en_GB
DICT en US en_US
DICT en ZA en_ZA
# Spanish variants
DICT es AR es_ES
DICT es BO es_ES
DICT es CL es_ES
DICT es CO es_ES
DICT es CR es_ES
DICT es CU es_ES
DICT es DO es_ES
DICT es EC es_ES
DICT es ES es_ES
DICT es GT es_ES
DICT es HN es_ES
DICT es MX es_ES
DICT es NI es_ES
DICT es PA es_ES
DICT es PE es_ES
DICT es PR es_ES
DICT es PY es_ES
DICT es SV es_ES
DICT es UY es_ES
DICT es VE es_ES
HYPH cs CZ hyph_cs_CZ
HYPH da DK hyph_da_DK
HYPH de CH hyph_de_CH
HYPH el GR hyph_el_GR
HYPH en US hyph_en_US
HYPH en CA hyph_en_CA
HYPH en AU hyph_en_AU
HYPH en GB hyph_en_GB
HYPH en BZ hyph_en_GB
HYPH en IE hyph_en_GB
HYPH en JM hyph_en_GB
HYPH en NZ hyph_en_GB
HYPH en PH hyph_en_GB
HYPH en ZA hyph_en_GB
HYPH en TT hyph_en_GB
HYPH en ZW hyph_en_GB
HYPH es ES hyph_es_ES
HYPH es GL hyph_es_ES
HYPH es AR hyph_es_ES
HYPH es BZ hyph_es_ES
HYPH es BO hyph_es_ES
HYPH es CL hyph_es_ES
HYPH es CO hyph_es_ES
HYPH es CR hyph_es_ES
HYPH es CU hyph_es_ES
HYPH es DO hyph_es_ES
HYPH es EC hyph_es_ES
HYPH es SV hyph_es_ES
HYPH es GT hyph_es_ES
HYPH es HN hyph_es_ES
HYPH es MX hyph_es_ES
HYPH es NI hyph_es_ES
HYPH es PA hyph_es_ES
HYPH es PY hyph_es_ES
HYPH es PE hyph_es_ES
HYPH es PR hyph_es_ES
HYPH es UY hyph_es_ES
HYPH es VE hyph_es_ES
HYPH fi BE hyph_fi_FI
HYPH fr FR hyph_fr_FR
HYPH fr CH hyph_fr_FR
HYPH fr MC hyph_fr_FR
HYPH fr LU hyph_fr_FR
HYPH fr BE hyph_fr_BE
HYPH fr CA hyph_fr_FR
HYPH ga IE hyph_ga_IE
HYPH id IS hyph_id_ID
HYPH is IS hyph_is_IS
HYPH it IT hyph_it_IT
HYPH nl NL hyph_nl_NL
HYPH pt PT hyph_pt_BR
HYPH pt PT hyph_pt_PT
HYPH ro RO hyph_ro_RO
HYPH ru RU hyph_ru_RU
HYPH sk SK hyph_sk_SK
HYPH sl SI hyph_sl_SI
HYPH sv SE hyph_sv_SE
HYPH uk UA hyph_uk_UA
HYPH en US hyph_en_US
THES en AU th_en_AU_v2
THES en US th_en_US_v2
THES en GB th_en_US_v2
## !!! END AUTOMATIC SECTION -- DO NOT CHANGE !!!

```

Thanks again for your reply.

---

### Post by astrojaxx on 2008-11-14
I have the same problem!

---

### Post by glitterball on 2008-12-16
I can report that I have the same problem also.

---

### Post by oscarsfriend on 2009-01-29
I know this maybe a little late for the people in this thread, but I just had the same problem and found this thread looking for a solution.  I was unable to find one but managed to figure it out myself, so I thought I'd share in case someone else comes looking for it.  (BTW, I am running OO3 on Intrepid/Easy Peasy 1.0)

[Edit: Note that trying to set the UK thesaurus in the language settings of OO3 does not work, at least not for me, as no option for a thesaurus shows up under the UK setting.] I checked /etc/openoffice.org/dictionary.1st had the correct entries, and it did, and in fact openoffice seems to ignore the file (I edited out all languages except UK/GB, and all the others still showed up, even if I wiped my ~/.openoffice.org directory).  So that was a no go.

However, there is a pretty simple fix:

```

cd /usr/share/myspell/dicts
sudo ln -s th_en_US_v2.dat th_en_GB_v2.dat
sudo ln -s th_en_US_v2.idx th_en_GB_v2.idx

```

The dictionary.1st file just tells OO to use the US thesaurus anyway, so this just does the same thing by creating links to the US files with the GB name.  Next time I ran OO the UK/US thesaurus was up and running with the UK language settings.

I hope this helps someone.

---

### Post by scouser73 on 2009-01-29
Click **Tools, Options, Languages, Writing Aids** Click **Edit** then click the **Language drop-down menu**, from there de-select all the languaes you want except the one you wish to keep.

[IMG][[IMG]http://img89.imageshack.us/img89/3523/thesaurusvd8.th.png[/IMG]](http://img89.imageshack.us/my.php?image=thesaurusvd8.png)[/IMG]

---

### Post by oscarsfriend on 2009-01-29
Just to clarify: Setting the language options did not work for me, as the thesaurus did not even show up for the UK language settings (I see it does for you), hence the reason I had to hack my way around it with the symlinks.  (EDIT: Unless you are suggesting that deselecting all the other languages makes the option for the UK thesaurus appear?)

---

### Post by scouser73 on 2009-01-29
I deselected all the other languages and only have English GB marked. You could give it a go mate, see if it works for you now.

---

### Post by paulchinnz on 2009-03-20
Thanks oscarsfriend: certainly helped me out, although curiously had to reboot after making those terminal entries for it to work.

---

### Post by Paul.Robinson on 2009-04-02
Many Thanks oscarsfriend. You are a star :KS, I've spent ages looking for the solution today. Your solution worked.

---

### Post by frootloop on 2009-04-14
I had the same problem after a recent upgrade to OpenOffice 3.01 from 2.x.
After much messing with confif files, styles etc...I read this :

[http://www.weeklywhinge.com/?p=69](http://www.weeklywhinge.com/?p=69)

All I did was install the UK Thesaurus found here ([http://www.weeklywhinge.com/files/en_GB_2_0_0.oxt),then](http://www.weeklywhinge.com/files/en_GB_2_0_0.oxt),then) went into tools - options - language settings - language and changed the default document language to English UK. Thesaurus worled fine after that!

---

### Post by FrenchyFungus on 2009-04-17
> **frootloop said:**
> I had the same problem after a recent upgrade to OpenOffice 3.01 from 2.x.
After much messing with confif files, styles etc...I read this :

[http://www.weeklywhinge.com/?p=69](http://www.weeklywhinge.com/?p=69)

All I did was install the UK Thesaurus found here ([http://www.weeklywhinge.com/files/en_GB_2_0_0.oxt),then](http://www.weeklywhinge.com/files/en_GB_2_0_0.oxt),then) went into tools - options - language settings - language and changed the default document language to English UK. Thesaurus worled fine after that!
Thanks, this worked for me.

Cheers.

---

### Post by uppercrustie on 2009-04-18
> **oscarsfriend said:**
> I know this maybe a little late for the people in this thread, but I just had the same problem and found this thread looking for a solution.  I was unable to find one but managed to figure it out myself, so I thought I'd share in case someone else comes looking for it.  (BTW, I am running OO3 on Intrepid/Easy Peasy 1.0)

[Edit: Note that trying to set the UK thesaurus in the language settings of OO3 does not work, at least not for me, as no option for a thesaurus shows up under the UK setting.] I checked /etc/openoffice.org/dictionary.1st had the correct entries, and it did, and in fact openoffice seems to ignore the file (I edited out all languages except UK/GB, and all the others still showed up, even if I wiped my ~/.openoffice.org directory).  So that was a no go.

However, there is a pretty simple fix:

```

cd /usr/share/myspell/dicts
sudo ln -s th_en_US_v2.dat th_en_GB_v2.dat
sudo ln -s th_en_US_v2.idx th_en_GB_v2.idx

```

The dictionary.1st file just tells OO to use the US thesaurus anyway, so this just does the same thing by creating links to the US files with the GB name.  Next time I ran OO the UK/US thesaurus was up and running with the UK language settings.

I hope this helps someone.

Brilliant! This solved it.

---

### Post by thebigob on 2009-05-21
> **oscarsfriend said:**
> I know this maybe a little late for the people in this thread, but I just had the same problem and found this thread looking for a solution.  I was unable to find one but managed to figure it out myself, so I thought I'd share in case someone else comes looking for it.  (BTW, I am running OO3 on Intrepid/Easy Peasy 1.0)

[Edit: Note that trying to set the UK thesaurus in the language settings of OO3 does not work, at least not for me, as no option for a thesaurus shows up under the UK setting.] I checked /etc/openoffice.org/dictionary.1st had the correct entries, and it did, and in fact openoffice seems to ignore the file (I edited out all languages except UK/GB, and all the others still showed up, even if I wiped my ~/.openoffice.org directory).  So that was a no go.

However, there is a pretty simple fix:

```

cd /usr/share/myspell/dicts
sudo ln -s th_en_US_v2.dat th_en_GB_v2.dat
sudo ln -s th_en_US_v2.idx th_en_GB_v2.idx

```The dictionary.1st file just tells OO to use the US thesaurus anyway, so this just does the same thing by creating links to the US files with the GB name.  Next time I ran OO the UK/US thesaurus was up and running with the UK language settings.

I hope this helps someone.]

Had the same problem this fixed it for me in seconds

Thanks so much

---

### Post by noteviljoe on 2009-05-28
> **frootloop said:**
> I had the same problem after a recent upgrade to OpenOffice 3.01 from 2.x.
After much messing with confif files, styles etc...I read this :

[http://www.weeklywhinge.com/?p=69](http://www.weeklywhinge.com/?p=69)

All I did was install the UK Thesaurus found here ([http://www.weeklywhinge.com/files/en_GB_2_0_0.oxt),then](http://www.weeklywhinge.com/files/en_GB_2_0_0.oxt),then) went into tools - options - language settings - language and changed the default document language to English UK. Thesaurus worled fine after that!

Thanks for this as this was really bugging me! I think that this is a better fix than the one suggesting the bodged that makes open office use the US thesaurus while using the UK dictionary as why would I want to use a US thesaurus??

---

### Post by SilverWave on 2009-12-03
> **oscarsfriend said:**
> ...

However, there is a pretty simple fix:

```

cd /usr/share/myspell/dicts
sudo ln -s th_en_US_v2.dat th_en_GB_v2.dat
sudo ln -s th_en_US_v2.idx th_en_GB_v2.idx

```

I hope this helps someone.

Yes it did!

Thanks :)

---

### Post by redro on 2010-01-03
Yeah that worked for me also - only took 3 hours to find a solution. And now I can't be bothered doing what I was originally intending to do with the thesaurus. But thanks anyway for putting up a solution.

Just use Google Docs in the future.

---

### Post by amoun on 2010-09-13
>  Originally Posted by frootloop:
I had the same problem after a recent upgrade to OpenOffice 3.01 from 2.x.
After much messing with confif files, styles etc...I read this :

[http://www.weeklywhinge.com/?p=69](http://www.weeklywhinge.com/?p=69)

All I did was install the UK Thesaurus found here ([http://www.weeklywhinge.com/files/en_GB_2_0_0.oxt),then](http://www.weeklywhinge.com/files/en_GB_2_0_0.oxt),then) went into tools - options - language settings - language and changed the default document language to English UK. Thesaurus worled fine after that!


Way to go [EEEPC 900 Hardy OO 3.1] ):P

---

