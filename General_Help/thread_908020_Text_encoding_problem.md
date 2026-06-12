---
title: "Text encoding problem"
date: 2008-09-02
forum: General Help
---

### Post by Luke771 on 2008-09-02
I installed Ubuntu 8.04 like one week ago reverting back from Slackware that is so much better in many ways but pays the price in ease to use (that's another story, anyway).
The problem is probably that I used the old /home partition because I wanted to keep my data and where possible my settings.

What happens is that Firefox doesn't show non-standard characters (used often when writing in languages other than English) like accented vowels etc, showing a question mark instead.

I double checked in the Preferences interface and saw that Firefox' defaulr character encoding is set to Unicode UTF-8, so my question is, what may be causing this encoding problem?
The System Locale is the default en_US and so is Firefox; however I sometimes read pages in other languages, I noticed this accented vowels problem but I didn't pay much attention to it until I had to contribute a translation update to [The Freenet project](http://freenetproject.org) and those who tested it says that their browsers also displayed question marks instead of accented vowels when using that translation.

Opening the translation file ( .properties file, java-style strings) in Gedit shows accented vowels properly.

---

### Post by Luke771 on 2008-09-02
*bump*
I seem to have an ability to post questions that stay unanswered... I guess my problem is that I can't explain my problem clearly enough. 

Let's see if I can make it shorter and clearer: 

Encoding in Firefox is set to UTF-8 but I see question marks instead of accented vowels. Also apostrophes and some more characters are displayed as question marks.
I did double check - characher encoding is set to UTF-8
I installed firefox-2 just to cross check: same problem.
It seems to be a Firefox-specific issue, gedit and open office don't have this problem.

A .properties file generated with Firefox (translation for a java app's web interface) had an obvious encoding problem; the question marks instead of accented vowels appeared in all the browser of the users who tried to use that translated interface.
Yet, when I opened the translation file in Gedit, accented vowels were displayed correctly.

---

