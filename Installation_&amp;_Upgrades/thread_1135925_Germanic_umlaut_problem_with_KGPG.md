---
title: "Germanic umlaut problem with KGPG"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by nv22nv on 2009-04-24
Hello,

I'm experiencing a problem with KGPG related to Germanic umlauts (mutated vowels, e.g. ä, ö, ü), or more generally speaking, with character encoding. This is what it's about:

When decrypting a message which has been created by a Windows user, umlauts are displayed as "boxes" (two ones for each umlaut; I don't know about messages written by linux users). It's the same the other way around, i.e. when a Windows user is trying to decrypt a message of mine.

A workaround for me is to manually change the encoding from UTF-8 to ISO-8859-1 after decrypting a message. I think that with this I'm rather close to the cause of the problem, but I just don't know what to do to get my messages into the correct character encoding automatically. Note: In all other applications, I don't have any problems with my character encoding, at least in those I've used up to now.

The problem didn't occur as long as I had Ubuntu Dapper. It was only after I updated to Feisty a rather long time ago that it started happening, and I have been bothered by this situation until now. (I've upgraded to Gutsy in the meantime.) Yet, I've got a feeling that the upgrade may not be an important part of the situation.

Could someone please help me? **Any advice is greatly appreciated.**
Thanks in advance for your help.

**Edit:** Can someone please rename the topic title to "Character encoding problem with KGPG"? This is probably a better description.

---

### Post by nv22nv on 2009-04-29
Any ideas, anyone? I'm rather desperate with this one... :(

---

### Post by JohnPta on 2009-04-29
> **nv22nv said:**
> Hello,

I'm experiencing a problem with KGPG related to Germanic umlauts (mutated vowels, e.g. ä, ö, ü), or more generally speaking, with character encoding. This is what it's about:

When decrypting a message which has been created by a Windows user, umlauts are displayed as "boxes" (two ones for each umlaut; I don't know about messages written by linux users). It's the same the other way around, i.e. when a Windows user is trying to decrypt a message of mine.

A workaround for me is to manually change the encoding from UTF-8 to ISO-8859-1 after decrypting a message. I think that with this I'm rather close to the cause of the problem, but I just don't know what to do to get my messages into the correct character encoding automatically. Note: In all other applications, I don't have any problems with my character encoding, at least in those I've used up to now. When you get a solution to that problem please let me also know.

The problem didn't occur as long as I had Ubuntu Dapper. It was only after I updated to Feisty a rather long time ago that it started happening, and I have been bothered by this situation until now. (I've upgraded to Gutsy in the meantime.) Yet, I've got a feeling that the upgrade may not be an important part of the situation.

Could someone please help me? **Any advice is greatly appreciated.**
Thanks in advance for your help.

**Edit:** Can someone please rename the topic title to "Character encoding problem with KGPG"? This is probably a better description.

Ok it is Not the most intelligent solution but it works for me. I type an "e" behind the letter where an "Umlaut" belongs and the spell checker will pick it up as a mistake and gives you the option of the correct word with an "Umlaut" It is not much of an answer to your question but it might help you for the time being.

---

### Post by nv22nv on 2009-04-29
JohnPta, thanks for your answer. Unfortunately, that really doesn't solve my problem, this is the workaround I'm currently using. Interesting to see that I'm not the only one having that kinf of problem though.

---

