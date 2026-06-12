---
title: "dead stick or do i have to reformat it somehow?  curious as to salvagability"
date: 2024-09-28
forum: Hardware
---

### Post by cryofreeze666 on 2024-09-28
ok, i had 2 ssd's in this computer.  one that was 250 gb for o.s.'s and drivers only, and the second for files.  i had problems that i polluted the forums with trying to solve the problem of freezing on the /dev/nvme0n1p2.  i was helped to realize that i needed to check that drive when someone asked if i could boot from a usb.  i flipped secondary drive to primary and now i have my computer running again. 

so is that a dead stick or because of the nvme is it just a formatting problem?   i mean it's a nothing cost to replace, i realize, at worst 50 bucks for a 250 gb, but i i didn't get to retire at 50 because i threw money at every problem.  was curious if it may be salvagable. i cant inxi and give you that ssd it's not in the computer.

my curiosity stems from this, how fragile are ssd's?  when i first decided to dump windows i tried many different linux kernals, each time i would choose the first setting for installation (all variations of the wording of erase and install (operating system name).  i tryed a minimum of at least 5 or 10 different operating systems for sure, if you count different versions of a similar o.s.  i guess i'm wondering if the new ssd's are as fragile as the old magnetic hd's when it came to how often you could reinstall o.s.'s.  that ssd was barely a year old and this computer isn't getting the use it once did while i'm learning linux.

specifics of problem:
1) would always freeze at /dev/nvme01p2: clean (# of files)/ (total file space), (# of blocks)/ (total) blocks

2) sometimes the computer would spaz out and run a bunch of lines before freezing at that journal recovery line, but it would always end there.

3) switching secondary stick to primary then installing o.s. solved problem.

---

### Post by bobunderwood99 on 2024-09-28
[B]                            "[ashaduri]("https://github.com/ashaduri")                           commented           [May 14, 2024]("https://github.com/ashaduri/gsmartcontrol/issues/4#issuecomment-2110081919")              

[/B]

                     [TABLE="class: d-block user-select-contain"]
[TR]
[TD="class: comment-body markdown-body js-comment-body"]           Thanks everyone for providing the outputs!
 GSmartControl now fully supports NVMe drives (yay!), including self-tests.
There are minor things missing still (like attribute warnings), but I  feel confident I can close this issue. Please open new issues if you  find major problems.

 Smartmontools 7.4 is required. Please note that NVMe support is still marked "experimental" in it.
 Meanwhile, please help me test the "main" branch. There  have been major changes in it (including defaulting to JSON parser for  all drives)."

[/TD]
[/TR]
[/TABLE]
                                                                                    
So, if you want a GUI SMART disk testing tool, install GSmartControl.

---

### Post by oldfred on 2024-09-28
What does this show? nvme - the NVMe storage command line interface utility (nvme-cli)

sudo apt install nvme-cli
nvme --help
sudo nvme list


Do you have latest firmware (FW revision) for your NVMe drives?
Compare to vendors support site for your version(s).

---

