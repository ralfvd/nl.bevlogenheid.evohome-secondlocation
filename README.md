### IMPORTANT NOTICE ###

If you are upgrading from version 1, you will need to re-enter your username and password in the app settings. Otherwise the app will not work. Also you might need to restart the app once after saving your username/password.

### Honeywell Evohome

With this app you can manage your Evohome and other systems that connect via Total Connect Comfort from within Homey. It is using the unofficial API of Evohome.

### Supported devices

The following devices are known to work with the app:

Control systems:

- Evohome ( + gateway RFG100 )
- Evohome Wifi
- Round Wireless ( + gateway RFG100 )

Thermostats (always in combination with Control system)

- HR92

Not in the list? It still could be supported; as long as your thermostat can be controlled via the Total Connect Comfort app, it should be controllable by the Homey app. Feedback is appreciated, so I can adjust the list.

### Settings
After installing the application, first visit the Homey Settings and navigate to the 'Honeywell Evohome' application.

Fill in your username (email address) and password and press save. Then, go to Devices and add a Honeywell Evohome device. Press thermostat and select which devices you'd like to add into Homey.

### Flow support

*Triggers*

- When temperature changes: triggers a flow when temperature changes
    - Via device card: individual temperature changes
    - Via Evohome card: any temperature measurement changes
- When target temperature changes: triggers a flow when the target temperature setting changes
    - Via device card: individual target temperature settings changes

*Conditions*

No conditions defined at this moment

*Actions*

- Set temperature ; this will set the individual temperature on a device. Attention: there is no way yet to cancel this setting other than setting another temperature or using the Evohome app/system.

- Reset temperature: Cancel individual device setting

- Execute QuickAction ; these are the generic settings of your Evohome. You can choose between:
    - Auto: this is the normal mode, Evohome will follow the set program
    - Economy: this is the economy mode, normally 3 degrees lower than Auto
    - Heating Off: This will turn your heating off ( with a lower limit of 7 degrees to protect the system from freezing )
    - Away: This will set the Evohome system to Away mode
    - Day Off: This will set the Evohome system to 'Day off' mode
    - Custom: This will set the Evohome system to 'Custom' mode; whatever you configured in Evohome itself

- Execute QuickAction (manual entry); with this card you can enter the quickaction yourself. This is usefull if you have stored a quickaction value in a variable in Homey, this can be used e.g. to restore a previous setting. e.g. door open, set quickaction for heating off, then when door closes, set quickaction with variable where the previous status was stored (e.g. Auto).

All actions are currently on 'permanent' mode. In the future there might be timers (e.g. set Economy for two hours). If you need that now, using the Homey built in-timers or the CountDown app to trigger a timed event.

### Acknowledgement

Initial scripting (based on HC2) provided by Webster
Icons provided by Webster & Reflow
Additional information by various sources on Internet

### Donate

If you like the app, consider a donation to support development  
[![Paypal donate][pp-donate-image]][pp-donate-link]

### Limitations

Only 1 Evohome system is supported.

### ToDo in order of my priority

- Add multiple location support
- Cancel all adjustments in an intelligent way to limit calls to Honeywell
- Add target temperature triggers
- Low battery detection
- Add hot water device support
- Check when heating mode is changing ( e.g. following  schedule , permament, etc)
- Clean-up code
- Time limits on quick Actions
- Time limits on temperature heatSetpoint
- Add timeout to code if Evohome service doesn't respond
- Add error checking in code
- Translation to NL

### Known bugs

In order of priority:

- Cancel adjustment doesn't work in Homey V2. ZoneId comes back as undefined
- LocationID cannot be retrieved correctly when login isn't completely successfull. In some instances this leads to errors. Workaround: restart app after saving username/Password
- When access token of Honeywell expires, the first login might give an error when reading status. Unsure if this also affects when updating; statistically changes are higher with the 5 minute interval. That's probably why I only see it during the regular_update.

### Unknown bugs

Yes ;-)

### Changelog

- V2.0.3 2018-01-17 : Bugfix for V2.0.1 ; not handling all cases, rewrite login procedure
- V2.0.2 2018-01-16 : Bugfixes, target setting via device card immediately visible in app
- V2.0.1 2018-01-15 : Bugfix when not having any devices
- V2.0.0 2018-01-15 : SDK2 enabled
- V1.0.6 2018-02-15 : Add supported devices in README
- V1.0.5 2017-11-21 : Evohome tag of temperature bugfix (number instead of string)
- V1.0.4 2017-09-05 : Ignore hot water devices in thermostat driver
- V1.0.3 2017-09-04 : Ignore reading of 128 degrees of thermostats (128 = controller received no input from thermostat)
- V1.0.2 2016-12-11 : Fixed bug in action card to use tokens for manual input
- V1.0.1 2016-12-05 : Action card to manually set the temperature instead of a slider
- V1.0.0 2016-11-19 : Quick Action setting and triggering working again
- V0.4.9 2016-11-16 : Bugfix for target_temperature reporting when setting the temperature via Homey. There is a maximum 5 minute delay before it shows in the device card and insight logging
- V0.4.8 2016-11-07 : Added target_temperature logging
- V0.4.7 2016-10-21 : Correct 'cancel temperature' implementation
- V0.4.6 2016-08-04 : Disabled quickaction checking due to API change
- V0.4.5 2016-07-22 : Removed some logging that cluttered the logging in settings
- V0.4.3 2016-06-15 : Solved 'first-run' bug
- V0.4.2 2016-06-14 : extra trigger & action cards, fixed bugs, first code clean-up
- V0.4.1 2016-06-09 : release for app store
- V0.3.6 2016-06-07 : insights logging added, pairing bugs solved
- V0.3.1 2016-06-05 : Second test release, including pairing of thermostats
- V0.0.1 2016-05-28 : First test release on Github

[pp-donate-link]: https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=ralf%40iae%2enl&lc=GB&item_name=homey%2devohome&item_number=homey%2devohome&currency_code=EUR&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted
[pp-donate-image]: https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif
