---
title: "Cannot Burn CD/DVD"
date: 2008-08-01
forum: General Help
---

### Post by Tekovro on 2008-08-01
i tried k3b, brasero, serpentine.. non of them seem to work.. i try to burn a cd and i get this error




BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    9.523s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x4 Hardware Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 9.488s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 255 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2273)

---

### Post by mc4man on 2008-08-01
Your getting an OPC error, OPC is optimum power calibration, basically before burning the drive is instructed to do a test write to small area on the disk reserved for this to determine the best laser setting for that particular media. Some possible solutions  include trying a different disk or brand of media, or getting some canned air and blowing out drive. (there always is possibility the drive is starting to fail)

If have or are familiar with wine you could install Imgburn and try a burn. It's a more sophisticated burning/iso creating prog. that should work 99% of the time.(and create /burn an iso in a proper manner with the right fs extensions 100% of the time). It also will allow you to disable the OPC ck. if it's still an issue.

if you haven't used wine and want to try imgburn then post back on that, there are a few things about getting it set up properly.

---

### Post by editrix on 2008-08-02
> **mc4man said:**
> if you haven't used wine and want to try imgburn then post back on that, there are a few things about getting it set up properly.

Hello mc4man, we meet again. I went to the imgburn site to check it out and it looks doable.

I'm thinking, since there are so many folks on this forum with burning problems, if imgburn can solve them, you might want to create a howto for the Tutorials & Tips section. In the meantime, yes, please, I'd like some advice from someone who knows the program. Also caveats: What one can't do with imgburn, if there's anything one can't do.

---

### Post by Tekovro on 2008-08-02
Thanks for the reply that was quite helpful. 

I installed IMGburn and i get this error as i click the write button




I changed the settings in I/O 

STPI to ASPI 

STPI(Microsoft) wasn't detecting my drive. then i read on a forum that changing it would solve the problem.

---

### Post by mc4man on 2008-08-02
@ Tekovro
I've never had problem with using STPI.   At times though with the later ver. of wine sometimes i've found starting Imgburn with a disk(s) in drive(s) is helpful if you get 'cannot detect drives' ( ones with a filesystem, then I'll switch to a blank disk after imgburn opens). 
My problem isn't with Imgburn but that wine kepts "losing" one of my drives and I've got to go to winecfg to re add.
I've now have also taken to having media in the drives and then doing the auto detect in winecfg -> drives
(_ck. your windows ver. as below_)

As far as your error, are you trying to burn a rw ? The error says OPC area is full, if you've burned it _alot_ of times maybe it is
Try unchecking 'perform opc before write' in tools -> settings -> write,  2nd option down in list on left. (should leave on in most cases) ( first screenshot 

@editrix
Regarding using it's pretty simple for basics, the default setting are good. The only changes I make 'for good' vs. specific tasks are in screenshots.

After installing wine run winecfg. As mentioned I'd put media in your drive(s) (anything but blank) and under the drives tab run autodetect and click apply.
Then on the applications tab for windows version choose _windows nt 4.0_ click apply and your good.
As i think I  mentioned to you let me know of any issues, ?'s ect., glad to help anyone wanting to use this 

link to some basic guides
[http://forum.imgburn.com/index.php?showforum=4](http://forum.imgburn.com/index.php?showforum=4)

reading the changelogs (whats new) provides alot of info on capabilities
[http://www.imgburn.com/](http://www.imgburn.com/)

note : if your using latest ver. of imgburn on hardy don't rotate your desktop if you can help it. While imgburn  continue fine the gui will disappear, the log box stays. Working on figuring out.

---

### Post by editrix on 2008-08-04
Hi mc4man:

I got the wine and imgburn downloaded and installed, but for some reason imgburn doesn't like the way I name files. Anyway, this is just a quickie to say I haven't given up hope. I just don't want to waste yet another CD by burning files I don't need archived onto it, so it's a question of organizing myself a little better. However, the program looks very promising.

Oh, two questions: Why NT4 as opposed to XP, which is how it defaulted?

And, by "don't rotate your desktop" do you as in Compiz, or just switch to another desktop? Because I don't use Compiz.

---

### Post by Tekovro on 2008-08-04
Thanks for all your help mc4man. It turns out the drive doesn't have anymore life left.. tested it on a different system and same thing. Just bought a new one for $30 so its no biggie.

---

