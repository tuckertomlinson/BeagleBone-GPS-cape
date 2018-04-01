PCB layout for a GPS cape for the beaglebone black.

This is a home project. There is NO garauntee that the circuits do what
is intended, or that the function is adequately documented.

Any use of the files found in this project should be accompanied by a 
thorough review to determine proper function and fitness for use.

Project goals:
- clock discipline for the Beaglebone family such that a beaglebone with cape
	may act as an NTP stratum1 timeserver on a local network
- Use a GPS module to generate a 1 PPS signal that is synced to the atomic 
	clocks. The GPS module should interface with an active antenna so that
	good satellite lock may be attained indoors.
- provide an accurate RTC via a stand-alone i2c RTC module
- Hardware will be provided on a PCB cape, using SMT components for tight layout
	and low cost.
- Provide a hardware overlay file that may be enabled in uEnv.txt that will 
	automatically configure the correct pins for PPS capture, and RTC 
	connection

Stretch goals:
- Included a voltage regulated clock source, and force the BB to use the external 
	clock for better frequency stability

Current status:
-Proof of concept based on Adafruit Ultimate GPS breakout constructed and working
-2 hardware capes designed
	-low cost cape based on Sierra Wireless XM1100 module
		-includeds RTC, and active antenna circuit
	-High cost cape based on uBlox LEA-M8T module
		-includes RTC, and 24Mhz VCTCXO clock. 
		-GPS module provides active antenna power
-Capes use Uart 4 to recieve GPS packets, and timer4 to take in PPS
-RTC is on i2c 1

Both capes completely untested.
