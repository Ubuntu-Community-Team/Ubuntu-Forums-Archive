---
title: "[SOLVED] spellcheck doesn't recognise british"
date: 2008-08-20
forum: General Help
---

### Post by leetrefz on 2008-08-20
I see packages for american and British spellcheck in synaptic but colour and metre get red lines. Can I make all English spellings accepted or how do I change from american to Commonwealth spelling?

---

### Post by coffeecat on 2008-08-20
Is there any other way to spell colour and metre? :roll: :wink:

Which application is this? If Open Office, go to Tools > Options > Language Settings > Language and change as appropriate. It should then use the UK English spellchecker.

---

### Post by leetrefz on 2008-08-20
The problem is in Firefox. I can't see any spellcheck options in it, or any firefox localisation packs in synaptic.

---

### Post by coffeecat on 2008-08-21
> **leetrefz said:**
> The problem is in Firefox.

I have a fix. In the firefox address bar, type 'about:config' (no quotes). Dismiss the childish 'here be dragons' warning and type 'spell' in the filter. The last option listed should be 'spellchecker.dictionary'. Change the value in the last column from en_US to en_GB. Close firefox and restart and you will pleased to find that 'colour' and 'metre' are not underlined, but that 'color' is.

If you want one of the Commonwealth variants of English, have a look in /usr/lib/locale to see what's available.

You'd think there would be a convenient GUI method to do this in Edit > preferences, but I couldn't find one.

---

### Post by tuxxy on 2008-08-21
> **coffeecat said:**
> Is there any other way to spell colour and metre? :roll: :wink:

Which application is this? If Open Office, go to Tools > Options > Language Settings > Language and change as appropriate. It should then use the UK English spellchecker.

Is it just me or has anyone noticed the OO spellchecker is rather poor...

---

### Post by coffeecat on 2008-08-21
> **tuxxy said:**
> Is it just me or has anyone noticed the OO spellchecker is rather poor...

Weel, I jsut tipped thsi ni OO adn I dodn't hafe any porbemls.

:wink:

---

### Post by tuxxy on 2008-08-21
> **coffeecat said:**
> Weel, I jsut tipped thsi ni OO adn I dodn't hafe any porbemls.

:wink:

:lolflag:

Seriously its that bad, I wonder when this will be improved enough for me not to have to double spell check every document in office :(

---

### Post by leetrefz on 2008-08-21
If I change it to anything but US I get no more spellchecking, even if I restart the whole computer. Is there a second setting I should check?

---

### Post by coffeecat on 2008-08-22
> **leetrefz said:**
> If I change it to anything but US I get no more spellchecking, even if I restart the whole computer. Is there a second setting I should check?

Are you referring to Firefox? 

Now I've tested it further, I'm getting some strange and inconsistent results. It seemed to work with a brief test in the quick reply box after I'd changed the setting to en_GB, but now I'm replying in the quote box, I get some redlines at first, and then it seems to give up most (but not all) of the time.

I don't know the answer. To be honest, I had never bothered with the spellchecker in Firefox before. (That's interesting - the first instance of 'Firefox' is redlined, the second not. :?) Anyway, all I can suggest now is the [Firefox support forum]("http://support.mozilla.com/en-US/kb/Support+Website+Forums"). There might be something there.

---

### Post by leetrefz on 2008-09-02
I fixed it, I think by installing myspell-en-GB or however it's correctly typed. If only firefox could check English and Russian simultaneosly. 

Why isn't this text box getting checked? is it java so impenetrable by the checker? Is there a way around that? Everything else I usually do is getting checked.

Is there a system wide spell check? I remember when I tried Mint it seemed to have that.

Nevermind that, if you right click on a misspelled word you can add a dictionary, and then select it. I'd like to know how to remove *hork* yank from the list but oh well. At least I can select Canadian or Russian now.

---

