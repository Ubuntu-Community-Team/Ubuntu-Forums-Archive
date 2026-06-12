---
title: "Wacom CTL470 and xorg problems"
date: 2012-11-25
forum: Hardware
---

### Post by letkajenkka on 2012-11-25
Hello,

Since upgrading Ubuntu from 10.10 via 11.4 and 11.10 to 12.04 I can't get wacom Bamboo 3 Pen (CTL-470) to work. Previously I followed all the steps suggested [here]("http://ubuntuforums.org/showthread.php?t=1780154") and it worked properly (in 10.10), but after all the upgrades it stopped. Now I tried repeating the steps, but it seems I must have messed something up, because now when I plug in the tablet the screen goes blank. 
Could anybody help me get xorg (or whatever I broke) to the former state and make the tablet work? I tried everything I could find on the net, all the steps from that thread, some drivers of a Chris, but nothing works. Thanks in advance.

---

### Post by Favux on 2012-11-25
Hi letkajenkka,

Welcome to Ubuntu forums!


I'm going to guess you updated your xf86-input-wacom in addition to input-wacom.  For Precise you need to patch xf86-input-wacom with the frankenserver patch otherwise plugging in your BambooPT will blow up your system.  See:  [http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034](http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034)  Or an [updated BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").

---

### Post by letkajenkka on 2012-11-25
> **Favux said:**
> Hi letkajenkka,

Welcome to Ubuntu forums!


I'm going to guess you updated your xf86-input-wacom in addition to input-wacom.  For Precise you need to patch xf86-input-wacom with the frankenserver patch otherwise plugging in your BambooPT will blow up your system.  See:  [http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034](http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034)  Or an [updated BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").
Thanks, but after attempting to patch it gives me an error "1 out of 1 hunk FAILED -- saving rejects to file test/fake-symbols.c.rej". I recloned the git repository and added --ignore-whitespace to the patching command, resulting in "Reversed (or previously applied) patch detected!  Assume -R? [n]", then it gave me the same error. :confused:

---

### Post by Favux on 2012-11-25
Hmm.  Not sure I've tested it on the 0.18.0 tar.  Will have to check if it works.

Not sure about the second error, sounds like you needed a make clean.  But it was a clean clone?

---

### Post by Favux on 2012-11-25
Alright I see it.  After 0.17.0:
```
#if GET_ABI_MAJOR(ABI_XINPUT_VERSION) >= 16
```
etc. got added below it.  So 0.18.0 does require a new patch.  But since it looks like the rest of the patch applies it would be simple enough to just delete that hunk of code at line 481:
```
/* This is not the same as the X server one, but it'll do for the tests */
#if GET_ABI_MAJOR(ABI_XINPUT_VERSION) >= 14
typedef struct _InputOption {
    struct _InputOption *next;
    char *key;
    char *value;
} InputOption;

InputOption*
input_option_new(InputOption *list, const char *key, const char *value)
{
	InputOption *new;

	new = calloc(1, sizeof(InputOption));
	new->key = strdup(key);
	new->value = strdup(value);
	new->next = list;
	return new;
}

void
input_option_free_list(InputOption **opts)
{
	InputOption *tmp = *opts;
	while(*opts)
	{
		tmp = (*opts)->next;
		free((*opts)->key);
		free((*opts)->value);
		free((*opts));
		*opts = tmp;
	}
}
#endif
```
Which is what the patch is trying to do.

---

### Post by Favux on 2012-11-25
Alright this patch works for me on 0.18.0.  Same commands except the patch command changes to:
```
patch -p1 < ~/Desktop/build_against_frankenserver_for0.18.patch
```
I'd appreciate hearing your results when you test it.

---

### Post by letkajenkka on 2012-11-26
> **Favux said:**
> Alright this patch works for me on 0.18.0.  Same commands except the patch command changes to:
```
patch -p1 < ~/Desktop/build_against_frankenserver_for0.18.patch
```
I'd appreciate hearing your results when you test it.

Thank you so much! It worked like a charm! :KS The patching went without any problems and now the tablet works properly. Thanks again. :D

---

### Post by Favux on 2012-11-26
Great!  Good work.  :)


Now to update the HOW TOs.  Thanks for bringing this to my attention.

---

