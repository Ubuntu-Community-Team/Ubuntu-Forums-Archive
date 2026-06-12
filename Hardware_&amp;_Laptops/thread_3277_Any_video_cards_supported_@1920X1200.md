---
title: "Any video cards supported @1920X1200?"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by PatrickS on 2004-11-04
I've been unsucessful at getting my Asus V7100 GeForce2-MX card to run at 1920X1200 even with the nvidia drivers.  The Windows driver supported that resolution, so I know it's possible with that card.

Is anybody able to get 1920X1200 resolution out of any card with this distribution?  If so, what card are you using, and how did you get it to that point?

1920X1200 is my LCD monitor's native resolution and the photos that I edit (my primary use for the computer) look distorted with the 1600X1200 that I'm able to get with my current card.  This is a show-stopper for me.

Thanks in advance for any replies.

Patrick

---

### Post by tfwo on 2004-11-04
It's not about the video card, it's the monitor settings. I used the following steps when I had widescreen:
1) comment HorizSync and VertRefresh in XF86Config-4 (they're autodetected on newer monitors nowadays).
2) Put the desired mode in front of every "Display" subsection, "Modes" field.
3) If it still runs in another resolution, you need the modeline. Either generate it with something like kvideogen (are there such tools in Ubuntu?), or google for it on xf86config/xorg.conf, you monitor and modeline keywords.

---

### Post by tanari on 2004-11-05
I have radeon 32 sdr and viewsonic p95f+, 1920X1200 setup by default :)

---

### Post by PatrickS on 2004-11-06
Thanks for the advice tfwo.  I've got the 1920X1200 resolution working.

I had to add a modeLine to the XF86Config-4 file and insert the 1920X1200 resolution in the Modes lines.  When I commented out the HorizSync and VertRefresh lines, I ended up with a non-working (black screen) and had to boot in recovery mode to uncoment them.

Section "Monitor"
	Identifier	"240T/240MP"
	HorizSync	30-90
	VertRefresh	50-75
	Option		"DPMS"
# Following line added (from Google search)
	ModeLine	"1920x1200" 193.2 1920 2048 2256 2592 1200 1201 1204 1242
EndSection


	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1600x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1600x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1600x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1600x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1600x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1600x1200" "1440x900"
	EndSubSection

---

