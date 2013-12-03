Job: Static analysis of Drupal code
===================================

Jenkins job template for creating jobs to perform static analysis of Drupal code.

This job template can be used to analyze both single modules and install profiles.

Changes since fork
===

This project is a fork from [Wulff](https://github.com/wulff/jenkins-template-drupal-static-analysis) with the following changes.

config.xml
-----------

Changed plot graph G - Average length from `Average Class Length (NCLOC),Average Method Length (NCLOC)` to `Average Class Length (LLOC),Average Function Length (LLOC)`.

This is done because the original template was used with [a different PHPLocTask](https://github.com/raphaelstolt/phploc-phing/blob/master/PHPLocTask.php) than [we are using](https://raw.github.com/phingofficial/phing/master/classes/phing/tasks/ext/phploc/PHPLocTask.php).

As a side effect all plugins have now been marked with a version, which is nice.

Dependencies
===

Jenkins version: 1.541

Jenkins plugins
---

* Checkstyle v3.38
* PMD v3.37
* DRY v2.38
* Tasks v4.38
* Plot v1.5

Other
---

* [Build xml](https://raw.github.com/wulff/phing-drupal-static-analysis/develop/build.xml) and the files and applications specified in there.


Known issues
===

Plot
---

Sometimes the [Plot plugin](https://wiki.jenkins-ci.org/display/JENKINS/Plot+Plugin) doesn't show the exclusion values when editing a Jenkins job. You can make them be displayed by clicking the "Load data from csv file" even though it is selected, or perhaps selecting "Load data from properties file" and then reselect "Load data from csv file". This won't remove the values.

WallDisplay
---

If you do not use the WallDisplay plugin you can replace

    <properties>
      <de.pellepelster.jenkins.walldisplay.WallDisplayJobProperty plugin="jenkinswalldisplay@0.6.21"/>
      <hudson.plugins.disk__usage.DiskUsageProperty plugin="disk-usage@0.23"/>
    </properties>

with 

    <properties/>
