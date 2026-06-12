---
title: "I cant burn a DVD"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by fathefner on 2007-05-07
It tells me 


imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 16759 
	media type	= 0
	speed		= 4
	track type		= 6
	track format	= 3
	output		= none
job (BraseroGrowisofs) set_source
imager (BraseroGrowisofs) set_output_type
recorder (BraseroGrowisofs) set_drive
imager (BraseroGrowisofs) set_output
imager (BraseroGrowisofs) unsupported operation (in brasero_imager_set_output at burn-imager.c:142)
job (BraseroGrowisofs) set_task
imager (BraseroGrowisofs) get_size
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_IwI2Fp/brasero_tmp_3Q5ORT
	-exclude-list
	/tmp/brasero_tmp_IwI2Fp/brasero_tmp_ZR5ORT
	-print-size
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_IwI2Fp/brasero_tmp_3Q5ORT -exclude-list /tmp/brasero_tmp_IwI2Fp/brasero_tmp_ZR5ORT -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
process (BraseroGrowisofs) stderr: Using _DB__000.AVI;1 for  /[DB]_Naruto_186_[3B0EA422].avi ([DB]_Naruto_189_[2856CA96].avi)
process (BraseroGrowisofs) stderr: Using _DB__001.AVI;1 for  /[DB]_Naruto_189_[2856CA96].avi ([DB]_Naruto_202-203-204_[0569376B].avi)
process (BraseroGrowisofs) stderr: Using _DB__002.AVI;1 for  /[DB]_Naruto_202-203-204_[0569376B].avi ([DB]_Naruto_187_[41F56877].avi)
process (BraseroGrowisofs) stderr: Using _DB__003.AVI;1 for  /[DB]_Naruto_187_[41F56877].avi ([DB]_Naruto_194.avi)
process (BraseroGrowisofs) stderr: Using _DB__004.AVI;1 for  /[DB]_Naruto_194.avi ([DB]_Naruto_195_[BFFE78CB].avi)
process (BraseroGrowisofs) stderr: Using _DB__005.AVI;1 for  /[DB]_Naruto_195_[BFFE78CB].avi ([DB]_Naruto_191_[E7923CB9].avi)
process (BraseroGrowisofs) stderr: Using _DB__006.AVI;1 for  /[DB]_Naruto_191_[E7923CB9].avi ([DB]_Naruto_206_[E009D660].avi)
process (BraseroGrowisofs) stderr: Using _DB__007.AVI;1 for  /[DB]_Naruto_206_[E009D660].avi ([DB]_Naruto_184_[229A765A].avi)
process (BraseroGrowisofs) stderr: Using _DB__008.AVI;1 for  /[DB]_Naruto_184_[229A765A].avi ([DB]_Naruto_182_[55E404F9].avi)
process (BraseroGrowisofs) stderr: Using _DB__009.AVI;1 for  /[DB]_Naruto_182_[55E404F9].avi ([DB]_Naruto_192_[B41EC78F].avi)
process (BraseroGrowisofs) stderr: Using _DB__00A.AVI;1 for  /[DB]_Naruto_192_[B41EC78F].avi ([DB]_Naruto_180_[CBBBE38A].avi)
process (BraseroGrowisofs) stderr: Using _DB__00B.AVI;1 for  /[DB]_Naruto_180_[CBBBE38A].avi ([DB]_Naruto_190_[39119B6C].avi)
process (BraseroGrowisofs) stderr: Using _DB__00C.AVI;1 for  /[DB]_Naruto_190_[39119B6C].avi ([DB]_Naruto_199_[0E7C67D6].avi)
process (BraseroGrowisofs) stderr: Using _DB__00D.AVI;1 for  /[DB]_Naruto_199_[0E7C67D6].avi ([DB]_Naruto_197_[DFB5F598].avi)
process (BraseroGrowisofs) stderr: Using _DB__00E.AVI;1 for  /[DB]_Naruto_197_[DFB5F598].avi ([DB]_Naruto_200_[00016DC4].avi)
process (BraseroGrowisofs) stderr: Using _DB__00F.AVI;1 for  /[DB]_Naruto_200_[00016DC4].avi ([DB]_Naruto_201_[0D7733C2].avi)
process (BraseroGrowisofs) stderr: Using _DB__00G.AVI;1 for  /[DB]_Naruto_201_[0D7733C2].avi ([DB]_Naruto_183_[0B261899].avi)
process (BraseroGrowisofs) stderr: Using _DB__00H.AVI;1 for  /[DB]_Naruto_183_[0B261899].avi ([DB]_Naruto_193.avi)
process (BraseroGrowisofs) stderr: Using _DB__00I.AVI;1 for  /[DB]_Naruto_193.avi ([DB]_Naruto_198_[639AADDC].avi)
process (BraseroGrowisofs) stderr: Using _DB__00J.AVI;1 for  /[DB]_Naruto_198_[639AADDC].avi ([DB]_Naruto_185_[D6A91FA1].avi)
process (BraseroGrowisofs) stderr: Using _DB__00K.AVI;1 for  /[DB]_Naruto_185_[D6A91FA1].avi ([DB]_Naruto_196_[EA9F2205].avi)
process (BraseroGrowisofs) stderr: Using _DB__00L.AVI;1 for  /[DB]_Naruto_196_[EA9F2205].avi ([DB]_Naruto_181_[AA81C51F].avi)
process (BraseroGrowisofs) stderr: Using _DB__00M.AVI;1 for  /[DB]_Naruto_181_[AA81C51F].avi ([DB]_Naruto_188_[C75E7923].avi)
process (BraseroGrowisofs) stderr: Total extents scheduled to be written = 2234695
growisofs (BraseroGrowisofs) set_total
process (BraseroGrowisofs) stdout: HUP
process (BraseroGrowisofs) stderr: HUP
job (BraseroGrowisofs) asked to stop
	status	= 0
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-speed=4
	-dvd-compat
	-use-the-force-luke=tty
	-use-the-force-luke=tracksize:2234695
	-Z
	/dev/scd0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_IwI2Fp/brasero_tmp_3Q5ORT
	-exclude-list
	/tmp/brasero_tmp_IwI2Fp/brasero_tmp_ZR5ORT
	-V
	Naruto
	-A
	Brasero-0.5.2
	-sysid
	LINUX
	-v
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_IwI2Fp/brasero_tmp_3Q5ORT -exclude-list /tmp/brasero_tmp_IwI2Fp/brasero_tmp_ZR5ORT -V Naruto -A Brasero-0.5.2 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
process (BraseroGrowisofs) stderr: genisoimage 1.1.2 (Linux)
process (BraseroGrowisofs) stderr: Using _DB__000.AVI;1 for  /[DB]_Naruto_186_[3B0EA422].avi ([DB]_Naruto_189_[2856CA96].avi)
process (BraseroGrowisofs) stderr: Using _DB__001.AVI;1 for  /[DB]_Naruto_189_[2856CA96].avi ([DB]_Naruto_202-203-204_[0569376B].avi)
process (BraseroGrowisofs) stderr: Using _DB__002.AVI;1 for  /[DB]_Naruto_202-203-204_[0569376B].avi ([DB]_Naruto_187_[41F56877].avi)
process (BraseroGrowisofs) stderr: Using _DB__003.AVI;1 for  /[DB]_Naruto_187_[41F56877].avi ([DB]_Naruto_194.avi)
process (BraseroGrowisofs) stderr: Using _DB__004.AVI;1 for  /[DB]_Naruto_194.avi ([DB]_Naruto_195_[BFFE78CB].avi)
process (BraseroGrowisofs) stderr: Using _DB__005.AVI;1 for  /[DB]_Naruto_195_[BFFE78CB].avi ([DB]_Naruto_191_[E7923CB9].avi)
process (BraseroGrowisofs) stderr: Using _DB__006.AVI;1 for  /[DB]_Naruto_191_[E7923CB9].avi ([DB]_Naruto_206_[E009D660].avi)
process (BraseroGrowisofs) stderr: Using _DB__007.AVI;1 for  /[DB]_Naruto_206_[E009D660].avi ([DB]_Naruto_184_[229A765A].avi)
process (BraseroGrowisofs) stderr: Using _DB__008.AVI;1 for  /[DB]_Naruto_184_[229A765A].avi ([DB]_Naruto_182_[55E404F9].avi)
process (BraseroGrowisofs) stderr: Using _DB__009.AVI;1 for  /[DB]_Naruto_182_[55E404F9].avi ([DB]_Naruto_192_[B41EC78F].avi)
process (BraseroGrowisofs) stderr: Using _DB__00A.AVI;1 for  /[DB]_Naruto_192_[B41EC78F].avi ([DB]_Naruto_180_[CBBBE38A].avi)
process (BraseroGrowisofs) stderr: Using _DB__00B.AVI;1 for  /[DB]_Naruto_180_[CBBBE38A].avi ([DB]_Naruto_190_[39119B6C].avi)
process (BraseroGrowisofs) stderr: Using _DB__00C.AVI;1 for  /[DB]_Naruto_190_[39119B6C].avi ([DB]_Naruto_199_[0E7C67D6].avi)
process (BraseroGrowisofs) stderr: Using _DB__00D.AVI;1 for  /[DB]_Naruto_199_[0E7C67D6].avi ([DB]_Naruto_197_[DFB5F598].avi)
process (BraseroGrowisofs) stderr: Using _DB__00E.AVI;1 for  /[DB]_Naruto_197_[DFB5F598].avi ([DB]_Naruto_200_[00016DC4].avi)
process (BraseroGrowisofs) stderr: Using _DB__00F.AVI;1 for  /[DB]_Naruto_200_[00016DC4].avi ([DB]_Naruto_201_[0D7733C2].avi)
process (BraseroGrowisofs) stderr: Using _DB__00G.AVI;1 for  /[DB]_Naruto_201_[0D7733C2].avi ([DB]_Naruto_183_[0B261899].avi)
process (BraseroGrowisofs) stderr: Using _DB__00H.AVI;1 for  /[DB]_Naruto_183_[0B261899].avi ([DB]_Naruto_193.avi)
process (BraseroGrowisofs) stderr: Using _DB__00I.AVI;1 for  /[DB]_Naruto_193.avi ([DB]_Naruto_198_[639AADDC].avi)
process (BraseroGrowisofs) stderr: Using _DB__00J.AVI;1 for  /[DB]_Naruto_198_[639AADDC].avi ([DB]_Naruto_185_[D6A91FA1].avi)
process (BraseroGrowisofs) stderr: Using _DB__00K.AVI;1 for  /[DB]_Naruto_185_[D6A91FA1].avi ([DB]_Naruto_196_[EA9F2205].avi)
process (BraseroGrowisofs) stderr: Using _DB__00L.AVI;1 for  /[DB]_Naruto_196_[EA9F2205].avi ([DB]_Naruto_181_[AA81C51F].avi)
process (BraseroGrowisofs) stderr: Using _DB__00M.AVI;1 for  /[DB]_Naruto_181_[AA81C51F].avi ([DB]_Naruto_188_[C75E7923].avi)
process (BraseroGrowisofs) stderr: Writing:   Initial Padblock                        Start Block 0
process (BraseroGrowisofs) stderr: Done with: Initial Padblock                        Block(s)    16
process (BraseroGrowisofs) stderr: Writing:   Primary Volume Descriptor               Start Block 16
process (BraseroGrowisofs) stderr: Done with: Primary Volume Descriptor               Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Joliet Volume Descriptor                Start Block 17
process (BraseroGrowisofs) stderr: Done with: Joliet Volume Descriptor                Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   End Volume Descriptor                   Start Block 18
process (BraseroGrowisofs) stderr: Done with: End Volume Descriptor                   Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Version block                           Start Block 19
process (BraseroGrowisofs) stderr: Done with: Version block                           Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Path table                              Start Block 20
process (BraseroGrowisofs) stderr: Done with: Path table                              Block(s)    4
process (BraseroGrowisofs) stderr: Writing:   Joliet path table                       Start Block 24
process (BraseroGrowisofs) stderr: Done with: Joliet path table                       Block(s)    4
process (BraseroGrowisofs) stderr: Writing:   Directory tree                          Start Block 28
process (BraseroGrowisofs) stderr: Done with: Directory tree                          Block(s)    2
process (BraseroGrowisofs) stderr: Writing:   Joliet directory tree                   Start Block 30
process (BraseroGrowisofs) stderr: Done with: Joliet directory tree                   Block(s)    2
process (BraseroGrowisofs) stderr: Writing:   Directory tree cleanup                  Start Block 32
process (BraseroGrowisofs) stderr: Done with: Directory tree cleanup                  Block(s)    0
process (BraseroGrowisofs) stderr: Writing:   Extension record                        Start Block 32
process (BraseroGrowisofs) stderr: Done with: Extension record                        Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   The File(s)                             Start Block 33
process (BraseroGrowisofs) stderr: /dev/scd0: engaging DVD-R DAO upon user request...
process (BraseroGrowisofs) stderr: /dev/scd0: reserving 2234695 blocks
process (BraseroGrowisofs) stderr: :-[ RESERVE TRACK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
process (BraseroGrowisofs) stderr: /dev/scd0: "Current Write Speed" is 1.0x1352KBps.
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
process (BraseroGrowisofs) stderr: :-( media is not formatted or unsupported.
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting

---

