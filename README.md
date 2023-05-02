# air-imager
Legacy graphical forensic imager written in Perl/Tk


--------------------------------------------------------------------------
              AIR - Automated Image & Restore v2.0.0
                           January, 2010
--------------------------------------------------------------------------

********  WARNING !!! USE THIS SOFTWARE AT YOUR OWN RISK!!! **************
I've tested and used the software and it works for me, but there is no
guarantee that it will work for you.  You can very easily DESTROY DATA
IRRECOVERABLY by using this software.  Do not even attempt using this
software unless you are VERY FAMILIAR with using dd(1) or dcfldd(1)
and are VERY FAMILIAR with the process of imaging hard drives and other
media.  While this program is intended to make the imaging process more
convenient, it cannot THINK for you.  If you mix up the source and
destination targets and accidentally overwrite the original evidence, there
is nothing I (or anyone else) can do for you.

DO NOT USE THIS SOFTWARE FOR ACTUAL PRODUCTION OR CASE WORK UNTIL YOU HAVE
THOUROUGHLY TESTED IT AND HAVE SATISFIED YOURSELF THAT IT DOES WHAT YOU
WANT IT TO DO.  I WILL NOT BE RESPONSIBLE FOR UNEXPECTED RESULTS OBTAINED
FROM THE USE OF THIS SOFTWARE WHETHER THEY ARE THE RESULT OF PROGRAM BUGS,
USER ERROR, HARDWARE FAILURES, OR ACTS OF GOD.  AGAIN, IF YOU USE THIS
SOFTWARE YOU DO SO AT YOUR OWN RISK AND ASSUME ALL RESPONSIBILITY FOR THE
RESULTS.
***************************************************************************

AIR is a graphical front-end for dd and dc3dd designed to make the task
of creating forensic images of digital media easier for investigators and
incident response personnel.  AIR is written in Perl/Tk and (at this time)
only supports Linux.  Features include:

- choice of using either dd or dc3dd
- image verification between source and copy via MD5 or SHA1-SHA512
- image compression/decompression via gzip/bzip2
- image over a TCP/IP network
- maintains a detailed session log
- supports SCSI tape drives
- wiping (zeroing) drives or partitions
- splitting images into user-defined segments

--------------------------------------------------------------------------
REQUIREMENTS:

1.) uudecode:  make sure you have the uudecode program on your system. You
can find out by typing "which uudecode" at a command prompt.  If it isn't 
found then you will need to install the sharutils package from your install
CD-ROMs or get it from your distro's web site.

2.) Linux Distributions:  AIR has been tested and should work with Ubuntu
and Gentoo Linux.  It should work with other distributions but may take
configuring.  Typically the challenge is to have the correct version of
Perl/Tk installed.

3.) The current version of Perl/Tk (804.028) introduced a bug that breaks
AIR.  There is a development version with a fix that is available from:
http://search.cpan.org/CPAN/authors/id/S/SR/SREZIC/Tk-804.028_502.tar.gz
The AIR installer will attempt to download and install this version, but
if you have a different version already installed, you may want to uninstall
it first to prevent possible issues.

INSTALLING:

1.) You need to be root or run via sudo since the installer will put most
stuff in /usr/local/bin.

2.) Unzip the install-air-x.x.x.gz file:
	$ gunzip install-air-x.x.x.gz

3.) The installer file is a SHAR (shell archive) file that needs to be
executable to work.  Then you simply run the script:
	$ chmod +x install-air-x.x.x
	$ sudo ./install-air-x.x.x   (or ./install-air as root)

4.) If Perl/Tk is not installed on your system, install-air will try
to go to the CPAN site to get it.  Once it downloads Perl/Tk it will
automatically unpack, compile and install it.  If you already have
the correct version of Perl/Tk installed, then install-air will skip this
step.

5.) install-air will unpack and install the following files:
	- air		: the main program/script
	- air-counter	: a counting buffer script used for progress updates
	- tailer	: a script that spawns and tracks tail processes
	- GNU split     : a version that allows numeric extensions
	- air-icons	: icons that air uses

6.) That's it!  Type 'sudo air' on the command-line to start.

--------------------------------------------------------------------------

MISCELLANEOUS NOTES:

AIR makes use of some programs that are recommended, but not required:
	- dc3dd	: enhanced dd created by the Defense Cyber Crime Center
	- nc		: (netcat) enables imaging over the network
	- cryptcat	: nc with encryption (www.farm9.org)

I wrote AIR for myself.  Partly because I wanted something fun to work on and
partly because I wanted a convenient way to do my imaging without worrying as
much about "fat-fingering" my dd command line... all while maintaining a log
of what was done.  A couple of the guys in my group said they wanted to try
it out and later said I should share it with others.  So, here it is.

Is it perfect?  No.  Is it bug-free?  No.  But then, I don't think any software
could answer "yes" to those two questions.  It works for me.  It may or may not
work for you.  No guarantees. Please refer to the warning at the top of this
document.
--------------------------------------------------------------------------
Project maintainer:
  Steve Gibson : steve@stevegibson.com, http://www.stevegibson.com

Contributors:
  Dr. Nanni Bassetti : digitfor@gmail.com, http://www.caine-live.net

Report problems, bugs, suggestions, comments, code improvements to:
  Steve Gibson
  steve@stevegibson.com
  http://air-imager.sourceforge.net
