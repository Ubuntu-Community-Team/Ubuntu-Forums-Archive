---
title: "Settings in local.conf overwritten?"
date: 2008-08-13
forum: General Help
---

### Post by Xerxes83 on 2008-08-13
I am a bit confused by the way the font-config works...

From the fonts-conf manual:
> **<alias>**

Alias elements provide a shorthand notation for the set of common match operations needed to substitute one font family for another. They contain a *<family>* element followed by optional *<prefer>*, *<accept>* and *<default>* elements. Fonts matching the <family> element are edited to prepend the list of <prefer>ed families before the matching *<family>*, append the <accept>able families after the matching *<family>* and append the *<default>* families to the end of the family list.
> <!--
	Provide required aliases for standard names
	Do these after the users configuration file so that any aliases there are used preferentially
-->
<alias>
	<family>serif</family>
	<prefer><family>Times New Roman</family></prefer>
</alias>

So did the author leave out some important information? Given the above I would think that:
> <alias>
	<family>serif</family>
	<prefer><family>Times New Roman</family></prefer>
	<prefer><family>DejaVu Serif</family></prefer>
</alias>
followed by the following in a later (higher-numbered) configuration file (e.g. 99-high-priority.conf)
> <alias>
	<family>serif</family>
	<prefer><family>Bitstream Vera Serif</family></prefer>
	<prefer><family>Thorndale AMT</family></prefer>
</alias>
would result in the list
> <alias>
	<family>serif</family>
	<prefer><family>Times New Roman</family></prefer>
	<prefer><family>DejaVu Serif</family></prefer>
	<prefer><family>Bitstream Vera Serif</family></prefer>
	<prefer><family>Thorndale AMT</family></prefer>
</alias>
instead of the expected (because later configuration files have a higher priority)
> <alias>
	<family>serif</family>
	<prefer><family>Bitstream Vera Serif</family></prefer>
	<prefer><family>Thorndale AMT</family></prefer>
	<prefer><family>Times New Roman</family></prefer>
	<prefer><family>DejaVu Serif</family></prefer>
</alias>
But the again, this [bug]("https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/149944") suggests otherwise...

I would be very grateful if someone could shed some light on this. So, what are the resulting priorities?

---

### Post by Xerxes83 on 2008-08-28
*bump*

---

