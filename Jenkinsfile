node {
 
   stage 'Checkout'   
     git url: 'https://github.com/sennerholm/doodleshop.git'
     sh "ls"
     sh "env"
   
   stage 'Build'
     echo 'Building...'
     sleep 3
 
 
    stage 'Small'
      parallel Small1: {
        echo 'Running unitests'
        sleep 2
    }, Small2: {
       echo 'Running integrationstests'
       sleep 2
    }, Small3: {
       echo 'Running smoketests'
       sleep 4
 
    },
    failFast: true
}
 
node {
   stage 'UAT'
   echo 'Deploy to UAT'    
   sleep 2
}
 
// NOTE! Do not use input in node block, will block real executors
input 'Manuella tester OK?' 
 
stage 'Production'
input 'OK att driftsätta i PRODUKTION?'     
 
node {
   stage 'Smoketest'
   sleep 2
   echo 'Smokestesting in prod'     
 
}
