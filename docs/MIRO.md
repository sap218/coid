# MIRO Guidelines

Below we follow the MIRO guidelines for reporting on an ontology [1]. 

---

**A. The basics**
  * A.1 Combined Ontology for Inflammatory Diseases (COID) v1.0.0
  * A.2 Ontology owner: [Samantha C Pendleton](https://github.com/sap218) (Institute of Cancer and Genomic Sciences, University of Birmingham, UK) | [samanfapc@gmail.com](mailto:samanfapc@gmail.com)
  * A.3 [License](https://github.com/sap218/coid/blob/master/LICENSE.md), which governs the permissions surrounding the ontology (CC BY 3.0)
  * A.4 Ontology under the appropriate filename `coid.owl`, full URL: https://github.com/sap218/coid/blob/master/coid.owl
  * A.5 GitHub repository: https://github.com/sap218/coid
  * A.6 Methodological framework: used [Protégé](https://protege.stanford.edu/) software for ontology building using ICD-10 and other biomedical ontologies. Synonym expansion followed the works of Pendleton et al. using the tf-idf statistical analysis to gain patient-preferred synonyms [2] from the [patient.info](https://patient.info/forums) forums. Additionally expanded with external domain-expert terms from [ClinicalBERT](https://github.com/kexinhuang12345/clinicalBERT), a pretrained word2vec model on MIMIC-III clinical letters.
  
**B. Motivation**
  * B.1 Ontology is required in research as there currently lacks a system for specifically only inflammatory disorders, symptoms, and layman-specific terms. The controlled vocabulary for these disorders are quite limited and current biomedical layman terms are not useful for NLP tasks as layman terms should be specific to the forum: the need for understanding the “patient-voice”.
  * B.2 COID is derived from ICD-10 structure and biomedical ontologies, which are currently limited in the inflammatory domain in terms of synonyms, whilst synonyms and layman terms exist, we curate more from the patient forums and additionally from ClinicalBERT.
  * B.3 Target audience are those in the research area looking at inflammatory conditions or the patient voice.

**C. Scope, requirements, development community**
  * C.1 The requirements of the ontology is to be an extensive vocabulary for inflammatory disorders, their associated diseases, symptoms, therapeutic interventions (medication, surgeries), investigations, complications, and more.
  * C.2 Development community: [Samantha C Pendleton](https://github.com/sap218) MSc (University of Birmingham, UK). In addition to Luke T Slater PhD (University of Birmingham, UK), Andreas Karwath PhD (University of Birmingham, UK), and Georgios V Gkoutos PhD (University of Birmingham, UK).
  * C.3 The [Issues](https://github.com/sap218/coid/issues) tracking system is to be used for future developements/requests/bugs/general inquiries.

**D. Knowledge acquisition**
  * D.1 Foundation built from ICD-10 codes: following the structure and then cross-reference to biomedical ontologies.
  * D.2 ICD-10 accessed via [WHO](https://icd.who.int/browse10/2016/en#/) - biomedical ontologies accessed via [OLS](https://www.ebi.ac.uk/ols/index) - patient forum access via [patient.info](https://patient.info/forums) - and ClinicalBERT accessed via [ClinicalBERT GitHub](https://github.com/kexinhuang12345/clinicalBERT)
  * D.3 The included inflammatory disorders were derived from: [ICD10Data](https://www.icd10data.com/ICD10CM/Index/I/Inflammation%2C_inflamed%2C_inflammatory) & [ICD LIST](https://icdlist.com/?t=icd10&s=inflammation)
  
**E. Ontology content**
  * E.1 Ontology is `OWL` format, if you don't know how to convert, ask creator for an alternative ontology format.
  * E.2 Specifically used Protégé to develop the ontology with Git version control.
  * E.3 Ontology metrics, as of 22-05-2021 version 1.0.0 (see [CHANGELOG.md](https://github.com/sap218/coid/blob/master/CHANGELOG.md)) there are a total of 1185 classes, 8439 relationships and axioms, 5164 annotations, including 1763 database cross-references, and 796 layperson synonyms, curated from ClinicalBERT and patient forum conversation.
  * E.4 Cross-references ontologies inclue: BFO, DOID, HPO, ICD-9, ICD-10, NCIT, ORDO, PATO, READCODES, SNOMED-CT, SYMP, and UBERON.
  * E.5 IRI for COID is: https://github.com/sap218/coid/blob/master/coid.owl#COID_00000.
  * E.6 Identifier generation policy: Protégé’s preferences schema is that ontology’s entities are to have the prefix “COID” followed by an underscore then a five digit number. All classes have COID prefix and own numeric identifier since COID avoids importing axioms from other ontologies.
  * E.7 Entity metadata policy: currently `exact`, `broad`, `narrow`, and `related` synonyms in the ontology are additional clinical/medical terms derived from biomedical ontologies. However `layperson` are the patient-preferred terms, in addition to the ClinicalBERT terms.
  * E.8 ICD-10 was somewhat used as an upper ontology in the sense that the structure is followed when describing the inflammatory conditions.
  * E.9 Currently, relationship `occurs in` in COID is cross-referenced to BFO. COID defined it's own: `characterised by`, `patient reported symptom`, and `symptom of`.
  * E.10 Axiom patterns are inferred from the ontology structure itself (`subclass`) and by defined relationships.

**F. Managing change**
  * F.1 Sustainability plan: COID is freely available on GitHub and the creator, Samantha C Pendleton, will constantly update/change based on expert opinion or via Issue notifications. Anyone from the community can suggest new terms, but with sufficient evidence/justification. Potentially users can `fork` the ontology and make their own changes, which then allows the creator to merge these changes. If often particular individuals are making positive/appropriate changes they can be given direct access to co-maintain the ontology with the creator.
  * F.2 There is the [CHANGELOG.md](https://github.com/sap218/coid/blob/master/CHANGELOG.md) to note down major changes to the ontology. In addition to [Issues](https://github.com/sap218/coid/issues) tracking system for entities to be removed/split/redefined, additionally we can annotate these entities as obsolete. 
  * F.3 Ontology will follow “semantic versioning” guidelines and that it will maintain as version 1 unless a major foundation change is made then it will become version 2. Otherwise additional terms/fixes will increment to version 1.1.0, and minor fixes will change to 1.0.1 over time.

**G. Quality Assurance**
  * G.1 Successful testing on the patient forum and ClinicalBERT embeddings. Also used Protégé’s HermiT (v1.4.3.456) reasoner to ensure a coherent and consistent ontology. 
  * G.2 Ontology is novel and first in basic inflammatory disorders. Additionally this method of building (tf-idf) was previous validated and our re-using proves a fast approach to synonym curation. COID meets the stated requirements as an ontology suitable for the biomedical domain in additon to capturing the patient voice. Moreover we show that not only is expert knowledge dervived from ontologies but also extracted from clinical letters.
  * G.3 An example of application is using the ontology to perform ROC AUC analysis on ClinicalBERT to observe how clinicians and patients discuss conditions, see [forum-patientinfo](https://github.com/sap218/forum-patientinfo) repository for the word2vec model. Additionally layman terms can be used for sentiment analysis on patient forum text. Future applications include using ICD-10 codes for GWAS analysis on the UK Biobank cohort and other electronic health databases - COID provides an implicit axiomatic structure for data annotated with ICD-10, ICD-9, READCODES or SNOMED-CT as these are included as cross-references in the ontology, enhancing the potential value of COID for searching and curating unstructured clinical data.
  * G.4 Ontology not yet available on ontology repositories however freely available on GitHub (awaiting manuscript acceptance).
  * G.5 Evidence of use: as soon as the manuscript is accepted the creator will include a reference/link here.
  
**References**

[1] Matentzoglu, N., Malone, J., Mungall, C., & Stevens, R. (2018). MIRO: guidelines for minimum information for the reporting of an ontology. Journal of Biomedical Semantics, 9(1), 6.

[2] Pendleton, S. C., Slater, L. T., Karwath, A., Gilbert, R. M., Davis, N., Pesudovs, K., Liu, X., Denniston, A. K., Gkoutos, G. V., & Braithwaite, T. (2021). Development and application of the ocular immune-mediated inflammatory diseases ontology enhanced with synonyms from online patient support forum conversation. Computers in Biology and Medicine, 135, 104542.
