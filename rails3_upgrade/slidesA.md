!SLIDE black-slide center top
# Rails3 Upgrade #
![unixmonkey](unixmonkey.gif)

* David Jones
* Indy.rb - Mar 9, 2011

!SLIDE title-slide
# Why upgrade? #

!SLIDE bullets incremental

* faster
* better sql
* less coupling
* support
* mountable apps

!SLIDE bullets incremental
# Where to start? #

* RVM

.notes Since we are working with both Rails 2 and 3, you'll need a good way to switch between what version you are running.

* Rails-Upgrade (github.com/rails/rails_upgrade)

.notes Jeremy MacAnally's plugin to grep through your code for deprecated stuff

* Check your dependencies

.notes Gems and plugins that work with rails3
.notes You'll probably have to upgrade, or swap out to a competing gem/plugin

!SLIDE
# WARNING: LIVE CODING! #
.notes git clone git@github.com:unixmonkey/daibatsu.git
.notes cd daibatsu
.notes script/plugin install http://github.com/rails/rails_upgrade.git
.notes rake rails:upgrade:check
.notes rake rails:upgrade:backup
.notes rvm use ree@daibatsu --create
.notes gem install rails --version '3.0'
.notes rails --version
.notes rails new ./
.notes Answer y to most of these (not layout)
.notes rails server
.notes   will complain missing sqlite3 & run bundle install
.notes bundle install
.notes rails server
.notes   will blow up on new_rails_defaults, delete it
.notes rails server
.notes   will boot, go to /, get index.html, delete it
.notes rails server
.notes   will blow up because mobile_device? is undefined,
.notes   get it from application_controller.rb.rails2 backup & reload
.notes Click take the survey
.notes Fix helper to make html_safe
.notes   see deprecation warning on f.error_messages
.notes   do what is says and
.notes rails plugin install git://github.com/rails/dynamic_form.git
.notes rails server (now it works)
.notes take the survey to make sure its working
.notes rake test (blows up on any_instance) - add mocha to gemfile
.notes rake test -all passing, but deprecation errors
.notes  fix <% style block helpers
.notes rake test, old router dsl deprecation
.notes rake rails:upgrade:routes
.notes   blows up can't parse map.root, fix to make, :controller => :surveys, :action => :index


!SLIDE bullets incremental
# Common Gotcha's #
* error\_messages\_for & f.error\_messages

.notes have been extracted into http://github.com/rails/dynamic\_form

* link\_to\_remote and other built-in-prototype helpers

.notes have been extracted into http://github.com/rails/prototype\_legacy\_helper

* <%= is html-escaped by default %>

.notes helpers that spit out html tags will need to be marked as .html_safe or <%= raw(output) %> will need to be used

* /lib is no longer in load path

.notes config.autoload_paths += %W( #{Rails.root}/lib )

!SLIDE
# Sources #
[omgbloglol.com/post/359147788](http://omgbloglol.com/post/359147788)
[railsupgradehandbook.com](http://railsupgradehandbook.com)
[blog.peepcode.com/tutorials/2010/live-coding-rails-3-upgrade](http://blog.peepcode.com/tutorials/2010/live-coding-rails-3-upgrade)
[jeremymcanally.com/rails3_why_and_how.pdf](http://jeremymcanally.com/rails3_why_and_how.pdf)
[guides.rails.info](http://guides.rails.info)

!SLIDE top center
# Thank you #
### David Jones
![unixmonkey](unixmonkey.gif)
### [unixmonkey.net](http://unixmonkey.net)
### [twitter.com/unixmonkey](http://twitter.com/unixmonkey)
### [github.com/unixmonkey](http://github.com/unixmonkey)