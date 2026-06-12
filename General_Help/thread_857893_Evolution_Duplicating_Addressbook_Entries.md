---
title: "Evolution Duplicating Addressbook Entries"
date: 2008-07-13
forum: General Help
---

### Post by herschen on 2008-07-13
This is going to be a bit long-winded, so I'm going to cut to the chase right now and then fill in details later: I have a Treo 680 that I've synchronized with Evolution, then through syncevolution-0.7 to scheduleworld.com. I'm really happy with this setup and I would be willing to write out the instructions in a second for other Palm users, however Evolution keeps making duplicates of my addressbook. It's hard to follow what's happening in Evolution; I noticed that some contacts get duplicated entirely (don't know what makes Evolution decide to do this) and other contacts have the "Work" and/or "Home" entries duplicated as an "Other" field that can only be accessed on the phone. On the computer, you see the "Other" field listed, but there is no entry to edit. Is there a fix for this (or is it an unresolved bug)?

Once this is done, I'm going to combine all this information into a HOWTO for connecting your Palm to an Internet-based service. I've found that the scheduleworld --- syncevolution --- evolution --- gnome-pilot --- palm is the easiest to use. I've been fiddling around with this for days; I tried kpilot to ics to GCAL (and then I had Sunbird connected remotely to GCAL), I tried GCALDaemon and googlecalendarsync. The weak link in that setup was kpilot (it screwed up the time of events in the calendar).

If only I could connect g-pilot to Thunderbird/Lightning to ScheduleWorld, I'd be one happy camper. (This may be a pain in the butt, but it's a lot better than the one choice on Windows: Palm Desktop)

---

### Post by dcstar on 2008-07-13
> **herschen said:**
> This is going to be a bit long-winded, so I'm going to cut to the chase right now and then fill in details later: I have a Treo 680 that I've synchronized with Evolution, then through syncevolution-0.7 to scheduleworld.com. I'm really happy with this setup and I would be willing to write out the instructions in a second for other Palm users, however Evolution keeps making duplicates of my addressbook. It's hard to follow what's happening in Evolution; I noticed that some contacts get duplicated entirely (don't know what makes Evolution decide to do this) and other contacts have the "Work" and/or "Home" entries duplicated as an "Other" field that can only be accessed on the phone. On the computer, you see the "Other" field listed, but there is no entry to edit. Is there a fix for this (or is it an unresolved bug)?
.........

You may want to try deleting the Evolution address books and then allowing the sync process to create them from fresh, that might get things behaving better.

---

### Post by herschen on 2008-07-13
Thanks for the quick response...I've done that and now I've now run into another weird problem. Originally the categories were copied to my computer. However, because of the duplicates, I deleted the addressbook in my phone (with a Palm program Mass Transit) and then copied the addressbook from my computer down. I then found that none of the new contacts were assigned to any category (Evolution's category list does not download down to the phone), so I then reassigned the categories in the phone (which had not been deleted by Mass Transit). Then I deleted the addressbook on the computer and specified in gnome-pilot that it should always 'Copy from PDA' and synchronized again. Now the categories don't show up at all in Evolution and when I do add them, they are deleted anytime I synchronize because I'm not letting changes on the computer affect the phone. And I don't plan to change this, cause I know that Evolution's going to screw things up. WTF? (That's the only logical question I can ask)

---

### Post by dcstar on 2008-07-13
> **herschen said:**
> Thanks for the quick response...I've done that and now I've now run into another weird problem. Originally the categories were copied to my computer. However, because of the duplicates, I deleted the addressbook in my phone (with a Palm program Mass Transit) and then copied the addressbook from my computer down. I then found that none of the new contacts were assigned to any category (Evolution's category list does not download down to the phone), so I then reassigned the categories in the phone (which had not been deleted by Mass Transit). Then I deleted the addressbook on the computer and specified in gnome-pilot that it should always 'Copy from PDA' and synchronized again. Now the categories don't show up at all in Evolution and when I do add them, they are deleted anytime I synchronize because I'm not letting changes on the computer affect the phone. And I don't plan to change this, cause I know that Evolution's going to screw things up. WTF? (That's the only logical question I can ask)

Possibly the Sync software doesn't have the correct data structures to match Evolution, time to report it as a bug I think.

---

### Post by herschen on 2008-07-13
[https://bugs.launchpad.net/bugs/154070]("https://bugs.launchpad.net/bugs/154070")

So the duplicate entries problem is obviously an Evolution issue...is the category list a gnome-pilot bug? I wish there any way to test this out by synchronizing gnome-pilot with a file rather than Evolution. I can't really pinpoint what program is not communicating properly since gnome-pilot only works with Evolution on Ubuntu. I could just submit the bug for both programs and let both fight over whose fault it is. :confused:

---

