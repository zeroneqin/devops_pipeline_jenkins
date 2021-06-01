# DevOps Pipeline for Jenkins(Include Quality Gate)



timestamps {
    try {
        node {

            stage('Check out') {
                echo "===============stage : Check out : start"
				
				//Checkout the code from git or others
				
                echo "===============stage : Check out : end"
            }


            stage('Build') {
                echo "===============stage : Build : start"
				if(isUnitTest ) { 
					build with unit test
                } 
				else {
					build without unit test
				}
				echo "===============stage : Build : end"
            }

            stage('Unit Test Quality Gate') {
                echo "===============stage : Unit Test Quality Gate : start"
				
				//Parse the unit test result and check the quality gate
				
                echo "===============stage : Unit Test Quality Gate : end"
            }


            stage('Code Static Scan') {
                echo "===============stage : Code Static Scan : start"
				
				//Call code static scan utility  to scan code
				
                echo "===============stage : Code Static Scan : end"
            }


            stage('Code Static Scan Quality Gate') {
                echo "===============stage : Code Static Scan Quality Gate : start"
				
                //Parse the static scan result and check the quality gate
				
                echo "===============stage : Code Static Scan Quality Gate : end"
            }
			

            stage('Code Security Scan') {
				echo "===============stage : Code Security Scan : start"
				
				//Call code security scan utility to scan code
				
                echo "===============stage : Code Security Scan : end"
            }
			
			stage('Code Security Scan Quality Gate') {
                echo "===============stage : Code Security Scan Quality Gate : start"
				
                //Parse the security scan result and check the quality gate
				
                echo "===============stage : Code Security Scan Quality Gate : end"
            }
			


            stage('Build Artifact') {
                echo "===============stage : Build Artifact : start"

				//Call build utility to build Artifact like bin, lib, image and so on
				
                echo "===============stage : Build Artifact : end"
            }


            stage('Artifact scan') {
                echo "===============stage : Artifact Scan : start"

				//Call artifact sccan utility to scan the artifact
                
                echo "===============stage : Artifact Scan : end"
            }


			stage('Artifact Scan Quality Gate') {
                echo "===============stage : Artifact Scan Quality Gate : start"
				
                //Parse the artifact scan result and check the quality gate
				
                echo "===============stage : Artifact Scan Quality Gate : end"
            }
  

            if (deployTo >= TEST_ENV) {
                stage('Test Env Deployment') {
                    echo "===============stage : Test Env Deployment : start"
				
					//Deploy to test env like test k8s
				
					echo "===============stage : Test Env Deployment : end"
                }
				
				if (runAPITest in Test Env) {
					stage('API Test in Test Env') {
						echo "===============stage : API Test : start"
				
						//Run API Test or Call API Test Service
				
						echo "===============stage : API Test : end"
					}
					
					stage('API Test in Test Env Quality Gate') {
						echo "===============stage : API Test Quality Gate : start"
				
						//Check the api test quality gate
				
						echo "===============stage : API Test Quality Gate : end"
					}
				}
				
				
				
				if (runStressTest in Test Env) {
					stage('Stress Test in Test Env') {
						echo "===============stage : Stress Test : start"
				
						//Run Stress Test or Call Stress Test Service
				
						echo "===============stage : Stress Test : end"
					}
					
					stage('Stress Test in Test Env Quality Gate') {
						echo "===============stage : Stress Test Quality Gate : start"
				
						//Check the stress test quality gate
				
						echo "===============stage : Stress Test Quality Gate : end"
					}
				}
				
				if (runUITest in Test Env) {
					stage('UI Test in Test Env') {
						echo "===============stage : UI Test : start"
				
						//Run UI Test or Call UI Test Service
				
						echo "===============stage : UI Test : end"
					}
					stage('UI Test in Test Env Quality Gate') {
						echo "===============stage : UI Test Quality Gate : start"
				
						//Check the UI test quality gate
				
						echo "===============stage : UI Test Quality Gate : end"
					}
				}
				
				//other test
				......
			}
			
			
			if (deployTo >= PRE_PRODUCTION_ENV) {
                stage('Pre Production Env Deployment') {
                    echo "===============stage : Pre Production Env Deployment : start"
				
					//Deploy to pre production env like pre production k8s
				
					echo "===============stage : Pre Production Env Deployment : end"
                }
				
				if (runAPITest in Pre Production Env) {
					stage('API Test in Pre Production Env') {
						echo "===============stage : API Test : start"
				
						//Run API Test or Call API Test Service
				
						echo "===============stage : API Test : end"
					}
					
					stage('API Test in Pre Production Env Quality Gate') {
						echo "===============stage : API Test Quality Gate : start"
				
						//Check the api test quality gate
				
						echo "===============stage : API Test Quality Gate : end"
					}
				}
				
				
				
				if (runStressTest in Pre Production Env) {
					stage('Stress Test in Pre Production Env') {
						echo "===============stage : Stress Test : start"
				
						//Run Stress Test or Call Stress Test Service
				
						echo "===============stage : Stress Test : end"
					}
					
					stage('Stress Test in Pre Production Env Quality Gate') {
						echo "===============stage : Stress Test Quality Gate : start"
				
						//Check the stress test quality gate
				
						echo "===============stage : Stress Test Quality Gate : end"
					}
				}
				
				if (runUITest in Pre Production Env) {
					stage('UI Test in Pre Production Env') {
						echo "===============stage : UI Test : start"
				
						//Run UI Test or Call UI Test Service
				
						echo "===============stage : UI Test : end"
					}
					stage('UI Test in Pre Production Env Quality Gate') {
						echo "===============stage : UI Test Quality Gate : start"
				
						//Check the UI test quality gate
				
						echo "===============stage : UI Test Quality Gate : end"
					}
				}
				
				//other test
				......

			}
			
			
			if (deployTo >= PRODUCTION_ENV) {
                stage('Production Env Deployment') {
                    echo "===============stage : Production Env Deployment : start"
				
					//Deploy to production env like pre production k8s
				
					echo "===============stage : Production Env Deployment : end"
                }
				
				if (runAPITest in Production Env) {
					stage('API Test in Production Env') {
						echo "===============stage : API Test : start"
				
						//Run API Test or Call API Test Service
				
						echo "===============stage : API Test : end"
					}
					
					stage('API Test in Pre Production Env Quality Gate') {
						echo "===============stage : API Test Quality Gate : start"
				
						//Check the api test quality gate
				
						echo "===============stage : API Test Quality Gate : end"
					}
				}
				
				
				
				if (runStressTest in Production Env) {
					stage('Stress Test in Production Env') {
						echo "===============stage : Stress Test : start"
				
						//Run Stress Test or Call Stress Test Service
				
						echo "===============stage : Stress Test : end"
					}
					
					stage('Stress Test in Production Env Quality Gate') {
						echo "===============stage : Stress Test Quality Gate : start"
				
						//Check the stress test quality gate
				
						echo "===============stage : Stress Test Quality Gate : end"
					}
				}
				
				if (runUITest in Production Env) {
					stage('UI Test in Production Env') {
						echo "===============stage : UI Test : start"
				
						//Run UI Test or Call UI Test Service
				
						echo "===============stage : UI Test : end"
					}
					stage('UI Test in Production Env Quality Gate') {
						echo "===============stage : UI Test Quality Gate : start"
				
						//Check the UI test quality gate
				
						echo "===============stage : UI Test Quality Gate : end"
					}
				}
				
				//other test
				......

			}
			

 
        }
    } catch (e) {
        //Set build to failure
		//record the error 
		//mail or im the error 
    } finally {
        echo 'Pipeline Complete'
    }
}

