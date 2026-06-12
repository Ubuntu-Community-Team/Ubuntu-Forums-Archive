---
title: "still no sound..pls help"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by mikecicc on 2008-01-12
I'm getting no sound out of my Gateway 4540GZ notebook, onboard sound...

I've ran the "lspci" in the terminal and it does show my audio card...i've followed all these steps from another forum..

[INDENT]Check chmod of /dev/dsp
In some occasions, sound is only available to root. To check this, open gnome terminal and type "sudo totem" (without quote and you can run other player if you want.) Play a music and check whether you can listen music. If you do, close the totem and type "sudo chmod 666 /dev/dsp" (without quote.)
If you still can't listen any sound check the next step.
Check whether the volume is mute
I know this is ridiculous. But it does happen.
If your sound problem still keep going, check the last step, where my sound problem was finally resolved.
Run alsamixer and turn off IEC related options
IEC is an input to certain high end sound cards that support optical (fiber optic) sound feed from such things as DVD players etc.. My sound card is SIS on board and certainly doesn't have ability of using IEC. But Ubuntu turned on those options by default.
To turn off those options, rum "alsamixer" (without quote) in gnome terminal. You can move around each option with your arrow key (right and left key.) Move to every IEC related options, turn off all of those options (use keyboard "m" to turn off.) After turning off hit "Esc" key to save, and type "sudo alsactl store" so that it is saved permanently.
	
[/INDENT]
	


would anyone be interested in getting me started on the right path to get my sound working, im very new to ubuntu..

thanks !

---

### Post by Crenfinkle on 2008-01-12
post the relevant ouput from lspci please.

---

### Post by vasiliymeshko on 2008-01-17
Open sound control panel and de-select 'External Amplifier' (You might have to add it from options first). After that, there should be no issues.

---

